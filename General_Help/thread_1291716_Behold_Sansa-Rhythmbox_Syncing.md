---
title: "Behold Sansa-Rhythmbox Syncing"
date: 2009-10-15
forum: General Help
---

### Post by GMWeezel on 2009-10-15
Hello Ubuntu community! I know there are a number of users that have long struggled with the issue of synchronizing Sansa devices in MSC mode with Rhythmbox. I finally got around to working on a solution and am nearly done with it. I am posting what I have here in the mean time. I've only been working on this for about an hour and am pausing because it's 1am here. I should be done with it tomorrow. It will include syncing not only files but it will also sync playlists, converting the Rhythmbox XML lists to the Sansa PLA format.

EDIT: I have finished my script for synchronizing Sansas with Rhythmbox. You probably only need to change the SANSA_DEVICE variable. Change it so that the folder is the directory that your Sansa player is located in when it is mounted. If you have a V1 Sansa, you may need to change "PLAYLIST_FORMAT" from M3U to PLA. If you don't know which version you have, leave it at M3U. If that doesn't work, then change it to PLA.

To choose which lists will be synchronized, in your home folder, make a text file called "sansa-playlists." If your Rhythmbox playlists are "Blues", "Jazz", and "Pop," the sansa-playlists file should look something like this:

EDIT 2: Okay, more changes -- will now automatically search for the Sansa Media Player, detect the playlist type it uses and present you with a list of playlists to sync.

EDIT 3: Updated version with full GUI.

```

#!/bin/bash

RHYTHMBOX_DIR="$HOME/.gnome2/rhythmbox" # Rhythmobx settings folder

DEVICE_MIRROR="$HOME/.sansa-mirror"     # Local Sansa mirror folder

MOUNT_FOLDERS="/media/ /mnt/"           # Removable media mount location(s)
                                        # - Tells the program where to start
                                        #   its search for Sansa devices

# SANSA_MOUNT="/media/SANSA E250"

# If SANSA_MOUNT is not defined, look for a Sansa and determine its version.
if [ ! "${SANSA_MOUNT+x}" ]
then
    SDK=$(find $MOUNT_FOLDERS -mindepth 2 -maxdepth 3 -iname "version.sdk")
    MAJOR_VER=$(grep -am1 "FW:" "$SDK" | sed "s/FW[^\.]\+\([0-9]\+\)\..*/\1/")
    if [ "$MAJOR_VER" -eq "1" ]
    then
        PLAYLIST_FORMAT="PLA"
    elif [ "$MAJOR_VER" -eq "2" ]
    then
        PLAYLIST_FORMAT="M3U"
    else
        zenity --warning --title "Sansa not found" --text \
        "Sorry but the script was unable to locate a $1 Sansa device."
        exit
    fi
    SANSA_MOUNT=$(echo "$SDK" | sed 's/\(.*\)\/.*/\1/')
fi

# If unix2dos is not available as a binary, we will define our own version.
if [ ! $(which unix2dos) ]
then
    function unix2dos {
        awk 'sub("$", "\r")' "$1" > "$1".dos
        mv "$1".dos "$1"
    }
fi

function toPLA {
    echo "PLP PLAYLIST" > tmp.pla
    echo "VERSION 1.20" >> tmp.pla
    echo "" >> tmp.pla

    for LINE in $(grep -v "^/" "$1")
    do
        echo "HARP, $LINE" | sed -e "s/\//\\\\/g" >> tmp.pla
    done
    unix2dos tmp.pla
    iconv -f ASCII -t UTF16LE -o tmp.pla.utf tmp.pla
    mv tmp.pla.utf tmp.pla
    mv tmp.pla "$DEVICE_MIRROR/PLAYLISTS/$2".PLA
    rm "$1"
}

function toM3U {
    echo -e "#EXTM3U\n\n" > tmp.pla
    for LINE in $(cat "$1")
    do
        if [ $(echo "$LINE" | grep "^/") ]
        then
            LINE=$(echo "$LINE" | cut -b2-)
            echo "#EXTINF:60,$LINE" >> tmp.pla
        else
            echo "$LINE" | sed -e "s/MUSIC\/\(.*\)/\1/g" >> tmp.pla
            echo "" >> tmp.pla
        fi
    done
    mv tmp.pla "$DEVICE_MIRROR/MUSIC/$2".M3U
    rm "$1"
}

cd "$RHYTHMBOX_DIR"
rm -rf "$DEVICE_MIRROR/PLAYLISTS"
mkdir -p "$DEVICE_MIRROR/MUSIC/cache"
mv "$DEVICE_MIRROR/MUSIC"/* "$DEVICE_MIRROR/MUSIC/cache"
INIT_IFS="$IFS"; IFS=$'\n'

if [ ! "${PLAYLISTS+x}" ]
then
    CHECK_LIST=$(grep "playlist name=.*type=.static" "playlists.xml" | \
        sed 's/.*name="\(.*\)\" type.*/TRUE\n\1/')

    PLAYLISTS=$(zenity --list --text "Which playlists should be copied?" \
        --column="Sync" --column="Playlist Title" --checklist --width=500 \
        --height=450 --title "[$PLAYLIST_FORMAT] $SANSA_MOUNT" \
        $CHECK_LIST | sed "s/|/\n/g")

    if [ ! "$PLAYLISTS" ]
    then
        exit
    fi
fi

(
for PLAYLIST in $PLAYLISTS
do
    echo "Generating content for playlist \"$PLAYLIST\"..."
    XML=`grep -i -A65536 "name=\"$PLAYLIST\"" playlists.xml | \
        grep -m1 -B65536 "/playlist"`

    XML_ESCAPED_FILE_LIST=`echo "$XML" | \
        sed -n "s/.*<location>file:\/\/\(.*\)<\/location>/\1/p"`

    ECHO_ESCAPED_FILE_LIST=`echo "$XML_ESCAPED_FILE_LIST" | \
        sed "s/%\([0-9a-fA-F]\+\)/\\\\\\x\1/g"`

    PURE_FILE_LIST=`echo -e "$ECHO_ESCAPED_FILE_LIST"`

    for SONG in $PURE_FILE_LIST
    do
        HASH=$(echo "$SONG" | cksum | cut -d" " -f1)
        EXTENSION=$(echo "$SONG" | sed "s/.*\.\(.*\)/\1/")
        FILENAME=$HASH.$EXTENSION

        # Attempts to guess the song title based on the file name. It assumes
        # that each file name is prefixed with the track number.
        TITLE=$(basename "$SONG" | \
            sed "s/[0-9]\+[ ]\?[- ][ ]\?\(.*\)/\1/;s/\..*//")
        echo -e "/$TITLE\nMUSIC/$FILENAME" >> "$DEVICE_MIRROR/$PLAYLIST"


        if [ -f "$DEVICE_MIRROR/MUSIC/cache/$FILENAME" ]
        then
            mv "$DEVICE_MIRROR/MUSIC/cache/$FILENAME" "$DEVICE_MIRROR/MUSIC"
        else
            cp -l "$SONG" "$DEVICE_MIRROR/MUSIC/$FILENAME"
        fi
    done

    if [ "$PLAYLIST_FORMAT" == "PLA" ]
    then
        mkdir -p "$DEVICE_MIRROR/PLAYLISTS"
        toPLA "$DEVICE_MIRROR/$PLAYLIST" "$PLAYLIST"
    else
        toM3U "$DEVICE_MIRROR/$PLAYLIST" "$PLAYLIST"
    fi
done

rm -rf "$DEVICE_MIRROR/MUSIC/cache"
IFS="$INIT_IFS"

# From Sujee Maniyam's script (http://sujee.net):
#     first copy the files
#     timestamps to be accurate within a second.  This is needed as Unix file
#     system has more accurate timestamps the VFAT file sytem of sansa
if [ "$PLAYLISTS" ]
then
    echo "Copying files to device..."
    rsync -trL  --modify-window=1 --delete "$DEVICE_MIRROR/MUSIC" \
        "$SANSA_MOUNT"

    # Only try to sync the PLAYLISTS folder if it exists.
    if [ -d "$DEVICE_MIRROR/PLAYLISTS" ]
    then
        rsync -trL  --modify-window=1 --delete "$DEVICE_MIRROR/PLAYLISTS" \
            "$SANSA_MOUNT"
    fi
fi
echo "Done."
) | zenity --title "Status" --width 500 --height 450 --text-info

```

---

### Post by hpxchan on 2009-12-20
Thanks GMWeezel!!  I've been wrestling with this one for a long time.  I'm ridiculously picky, so I didn't actually end up using your code, but you inspired me to take another shot.

I wanted to be able to automatically back up all of my Rhythmbox playlists to .m3u format (more or less) in a specified folder.  I also wanted to be able to specify a subset of those playlists, and have that subset be synced with my 8GB Fuze (I don't use the expansion slot).  I couldn't have a local mirror of the Fuze due to there not being enough room on my hard drive.  To accommodate these needs, I came up with two Python scripts:  One to back up the playlists and one to sync the Fuze.  I don't think many people would prefer these over your easier-to-use and more capable script, but here they are just in case.

Please don't set [FONT=Courier New]PORTABLE_MUSIC='/'[/FONT], don't use this code in your military satellite navigation software, and in general don't do anything that would make you want to sue me.  Public domain.

save_rb_playlists.py
```

#!/usr/bin/python3


# This script exports all of the static playlists from Rhythmbox to
# M3U format (without the EXTINF bits) in a given directory.  

# Note:  The script was designed for Rhythmbox version 1.6.  It should
# work for any version of Rhythmbox whose playlists.xml file is
# compatible with version 1.6.


import urllib.parse
import os.path
import xml.dom.minidom


# Location of Rhythmbox's playlists.xml file.  We assume Rhythmbox
# version 1.6 (or any version whose playlists.xml file is compatible
# with version 1.6).
RHYTHMBOX_PLAYLISTS = os.path.expanduser('~/.local/share/rhythmbox/'
                                         'playlists.xml')
# Directory where playlists are stored on the local machine.
PLAYLISTS_DIR = os.path.expanduser('~/Documents/playlists/')


def check_node_name(node, name):
    if node.nodeName != name:
        raise Exception('Expected "%s" node but got "%s".' 
                        % (name, node.nodeName))

def main():
    if not PLAYLISTS_DIR.endswith('/'):
        raise Exception('PLAYLISTS_DIR must end with a /.')
    
    with open(RHYTHMBOX_PLAYLISTS) as doc:
        dom = xml.dom.minidom.parse(doc)
        rhythmdb_playlists = dom.firstChild
        check_node_name(rhythmdb_playlists, 'rhythmdb-playlists')
        for p in rhythmdb_playlists.childNodes:
            if (p.nodeType == p.ELEMENT_NODE
                and p.attributes['type'].value == 'static'):
                check_node_name(p, 'playlist')
                # This is an actual static playlist node, not some silly
                # text node or automatic/queue playlist node.
                playlist_name = p.attributes['name'].value
                playlist_fn = os.path.join(PLAYLISTS_DIR, 
                                           playlist_name + '.m3u')
                print('Putting %s.' % playlist_fn)
                song_lines = ['#EXTM3U\n']
                for s in p.childNodes:
                    if s.nodeType == s.ELEMENT_NODE:
                        check_node_name(s, 'location')
                        song_uri = s.firstChild.nodeValue.strip()
                        if song_uri.startswith('file://'):
                            song_fn = urllib.parse.unquote(song_uri[7:])
                            if not os.path.isfile(song_fn):
                                raise Exception('Song "%s" in playlist "%s" '
                                                'does not seem to exist.' 
                                                % (song_fn, playlist_name))
                            song_lines.append(song_fn + '\n')
                with open(playlist_fn, 'w') as pl_file:
                    pl_file.writelines(song_lines)


if __name__ == '__main__':
    main()

```sync_fuze.py
```

#!/usr/bin/python3


# This script syncs a collection of M3U playlists to a portable music
# player (which has MSC mode or can otherwise be accessed like a
# directory in the filesystem).  It was designed for the Sansa Fuze,
# firmware version V01.01.15A, so playlists are formatted for that
# particular device.

# Note:  The script does not look for changes to a given file (no 
# checksums are computed).  If you e.g. change the ID3 tag of a song
# on your local machine, you will need to delete the old version on the
# portable player in order for the new version to be synced.


import os.path
import os
import shutil


# Directory where playlists are stored on the local machine.
PLAYLISTS_DIR = os.path.expanduser('~/Documents/playlists/')
# Music directory on the local machine.
LOCAL_MUSIC = os.path.expanduser('~/Music/')
# Music directory on the portable player.  Note that .m3u files
# for synced playlists will be placed in this directory.
PORTABLE_MUSIC = '/media/0123-4567/MUSIC/'

# The songs in these playlists will be synced.  The playlists
# themselves (the .m3u files) will also be synced.
IMPORT_PLAYLISTS = ('l', 'm', 'n', 't')
# The songs in these playlists will be synced.  The playlists
# themselves will NOT be synced.
IMPORT_OTHER = ('o',)


def main():
    if not LOCAL_MUSIC.endswith('/'):
        raise Exception('LOCAL_MUSIC must end with a /.')
    if not PLAYLISTS_DIR.endswith('/'):
        raise Exception('PLAYLISTS_DIR must end with a /.')
    if not PORTABLE_MUSIC.endswith('/'):
        raise Exception('PORTABLE_MUSIC must end with a /.')
    
    playlists = []
    
    # Extract songs from the specified playlists.
    for pl in IMPORT_PLAYLISTS + IMPORT_OTHER:
        with open(os.path.join(PLAYLISTS_DIR, pl + '.m3u')) as pl_file:
            pl_songs = []
            for line in pl_file.readlines():
                l = line.strip()
                if not l.startswith('#'):
                    if not l.startswith(LOCAL_MUSIC):
                        raise Exception('Song "%s" in playlist "%s" is not in '
                                        'LOCAL_MUSIC, violating our '
                                        'assumption.' % (l, pl))
                    if not os.path.isfile(l):
                        raise Exception('Song "%s" in playlist "%s" does not '
                                        'seem to exist.' 
                                        % (l, pl))
                    pl_songs.append(l[len(LOCAL_MUSIC):])
            playlists.append(pl_songs)
    
    # Delete files in the portable music directory that are not in any
    # of the playlists.
    for root, dirs, files in os.walk(PORTABLE_MUSIC, topdown=False):
        for f in files:
            f_path = os.path.join(root, f)
            f_tail = f_path[len(PORTABLE_MUSIC):]
            if True not in ((f_tail in pl_songs) for pl_songs in playlists):
                # This file is not in any of the playlists.
                print('Removing %s.' % f_path)
                os.remove(f_path)
        for d in dirs:
            d_path = os.path.join(root, d)
            if not os.listdir(d_path):
                # This directory is empty.
                print('Removing %s.' % d_path)
                os.rmdir(d_path)
    
    # Add files from the playlists to the portable music directory
    # (unless they are already there).
    for pl_songs in playlists:
        for song in pl_songs:
            song_portable = os.path.join(PORTABLE_MUSIC, song)
            if not os.path.isfile(song_portable):
                # Song isn't already in the portable music directory,
                # so put it there.
                song_local = os.path.join(LOCAL_MUSIC, song)
                song_portable_dir = os.path.dirname(song_portable)
                print('Putting %s.' % song_portable)
                if not os.path.isdir(song_portable_dir):
                    os.makedirs(song_portable_dir)
                shutil.copy(song_local, song_portable)
    
    # Add the playlists themselves (the .m3u files) to the portable
    # music directory.
    for i in range(len(IMPORT_PLAYLISTS)):
        pl = IMPORT_PLAYLISTS[i]
        pl_songs = playlists[i]
        pl_portable = os.path.join(PORTABLE_MUSIC, pl + '.m3u')
        print('Putting %s.' % pl_portable)
        with open(pl_portable, 'w') as pl_file:
            # Use relative paths with DOS-like directory separators
            # and line ends.
            pl_file.write('#EXTM3U\r\n')
            pl_file.writelines(song.replace('/', '\\') + '\r\n' 
                               for song in pl_songs)


if __name__ == '__main__':
    main()

```The scripts use Python 3 because the urllib.unquote in Python 2.6 wasn't doing it for me.  I of course welcome any feedback.  GMWeezel, thanks again for the inspiration!  :)

Chandler

---

### Post by trikster_x on 2010-01-16
Figured out why it deleted all my music.  See my next post for minor details.  Playlist is still empty when synced, though.

---

### Post by GMWeezel on 2010-01-17
Hello trikster_x, the Sansa Clip I developed this on is a firmware version 2. I would be more than happy to fix the script for you but it will be a bit before I can get back on Linux. Do you know enough about bash scripting to make the script give you the output from rsync so that you could paste it here? Also, could you run "tree" on the folder that your MP3 player is mounted on?

---

### Post by trikster_x on 2010-01-18
Wow, I wasn't expecting a response or anything, I just wanted to prevent the headache I endured yesterday for someone else.  Thanks for checking up on this thread GMWeezel!!!

Unfortunately I am not at the point in my knowledge of bash scripting to perform more than the simplest tasks. Not sure if this is what you wanted, but I set the -v option in rsync.  This is what was printed when I ran the program:

```
Generating content for playlist "test"...
Copying files to device...
building file list ... done
MUSIC/
MUSIC/test.M3U

sent 166 bytes  received 48 bytes  428.00 bytes/sec
total size is 54  speedup is 0.25
Done.

```

I also removed the --delete option on a hunch and it did not delete my entire music library this time, so woot on that.
The playlist is still showing up empty on my device, though.

This is what tree looks like when the device is blank.

```
alex@alex-desktop:~$ tree /media/disk
/media/disk
|-- AUDIBLE
|-- AUDIOBOOKS
|-- MUSIC
|-- PLAYLISTS
|-- PODCASTS
`-- RECORD
    |-- FM
    `-- VOICE
|-- MTABLE.SYS
|-- RES_INFO.SYS
|-- SYS_CONF.SYS
|-- version.sdk
|-- WMPInfo.xml

```



Again, thank you for taking some time out to give me some support on this.:D

This is my modified version of the script:

```
#!/bin/bash

RHYTHMBOX_DIR="$HOME/.gnome2/rhythmbox" # Rhythmobx settings folder

DEVICE_MIRROR="$HOME/.sansa-mirror"     # Local Sansa mirror folder

MOUNT_FOLDERS="/media/ /mnt/"           # Removable media mount location(s)
                                        # - Tells the program where to start
                                        #   its search for Sansa devices

# SANSA_MOUNT="/media/SANSA E250"

# If SANSA_MOUNT is not defined, look for a Sansa and determine its version.
if [ ! "${SANSA_MOUNT+x}" ]
then
    SDK=$(find $MOUNT_FOLDERS -mindepth 2 -maxdepth 3 -iname "version.sdk")
    MAJOR_VER=$(grep -am1 "FW:" "$SDK" | sed "s/FW[^\.]\+\([0-9]\+\)\..*/\1/")
    if [ "$MAJOR_VER" -eq "1" ]
    then
        PLAYLIST_FORMAT="PLA"
    elif [ "$MAJOR_VER" -eq "2" ]
    then
        PLAYLIST_FORMAT="M3U"
    else
        zenity --warning --title "Sansa not found" --text \
        "Sorry but the script was unable to locate a $1 Sansa device."
        exit
    fi
    SANSA_MOUNT=$(echo "$SDK" | sed 's/\(.*\)\/.*/\1/')
fi

# If unix2dos is not available as a binary, we will define our own version.
if [ ! $(which unix2dos) ]
then
    function unix2dos {
        awk 'sub("$", "\r")' "$1" > "$1".dos
        mv "$1".dos "$1"
    }
fi

function toPLA {
    echo "PLP PLAYLIST" > tmp.pla
    echo "VERSION 1.20" >> tmp.pla
    echo "" >> tmp.pla

    for LINE in $(grep -v "^/" "$1")
    do
        echo "HARP, $LINE" | sed -e "s/\//\\\\/g" >> tmp.pla
    done
    unix2dos tmp.pla
    iconv -f ASCII -t UTF16LE -o tmp.pla.utf tmp.pla
    mv tmp.pla.utf tmp.pla
    mv tmp.pla "$DEVICE_MIRROR/PLAYLISTS/$2".PLA
    rm "$1"
}

function toM3U {
    echo -e "#EXTM3U\n\n" > tmp.pla
    for LINE in $(cat "$1")
    do
        if [ $(echo "$LINE" | grep "^/") ]
        then
            LINE=$(echo "$LINE" | cut -b2-)
            echo "#EXTINF:60,$LINE" >> tmp.pla
        else
            echo "$LINE" | sed -e "s/MUSIC\/\(.*\)/\1/g" >> tmp.pla
            echo "" >> tmp.pla
        fi
    done
    mv tmp.pla "$DEVICE_MIRROR/MUSIC/$2".M3U
    rm "$1"
}

cd "$RHYTHMBOX_DIR"
rm -rf "$DEVICE_MIRROR/PLAYLISTS"
mkdir -p "$DEVICE_MIRROR/MUSIC/cache"
mv "$DEVICE_MIRROR/MUSIC"/* "$DEVICE_MIRROR/MUSIC/cache"
INIT_IFS="$IFS"; IFS=$'\n'

if [ ! "${PLAYLISTS+x}" ]
then
    CHECK_LIST=$(grep "playlist name=.*type=.static" "playlists.xml" | \
        sed 's/.*name="\(.*\)\" type.*/TRUE\n\1/')

    PLAYLISTS=$(zenity --list --text "Which playlists should be copied?" \
        --column="Sync" --column="Playlist Title" --checklist --width=500 \
        --height=450 --title "[$PLAYLIST_FORMAT] $SANSA_MOUNT" \
        $CHECK_LIST | sed "s/|/\n/g")

    if [ ! "$PLAYLISTS" ]
    then
        exit
    fi
fi

(
for PLAYLIST in $PLAYLISTS
do
    echo "Generating content for playlist \"$PLAYLIST\"..."
    XML=`grep -i -A65536 "name=\"$PLAYLIST\"" playlists.xml | \
        grep -m1 -B65536 "/playlist"`

    XML_ESCAPED_FILE_LIST=`echo "$XML" | \
        sed -n "s/.*<location>file:\/\/\(.*\)<\/location>/\1/p"`

    ECHO_ESCAPED_FILE_LIST=`echo "$XML_ESCAPED_FILE_LIST" | \
        sed "s/%\([0-9a-fA-F]\+\)/\\\\\\x\1/g"`

    PURE_FILE_LIST=`echo -e "$ECHO_ESCAPED_FILE_LIST"`

    for SONG in $PURE_FILE_LIST
    do
        HASH=$(echo "$SONG" | cksum | cut -d" " -f1)
        EXTENSION=$(echo "$SONG" | sed "s/.*\.\(.*\)/\1/")
        FILENAME=$HASH.$EXTENSION

        # Attempts to guess the song title based on the file name. It assumes
        # that each file name is prefixed with the track number.
        TITLE=$(basename "$SONG" | \
            sed "s/[0-9]\+[ ]\?[- ][ ]\?\(.*\)/\1/;s/\..*//")
        echo -e "/$TITLE\nMUSIC/$FILENAME" >> "$DEVICE_MIRROR/$PLAYLIST"


        if [ -f "$DEVICE_MIRROR/MUSIC/cache/$FILENAME" ]
        then
            mv "$DEVICE_MIRROR/MUSIC/cache/$FILENAME" "$DEVICE_MIRROR/MUSIC"
        else
            cp -l "$SONG" "$DEVICE_MIRROR/MUSIC/$FILENAME"
        fi
    done

    if [ "$PLAYLIST_FORMAT" == "PLA" ]
    then
        mkdir -p "$DEVICE_MIRROR/PLAYLISTS"
        toPLA "$DEVICE_MIRROR/$PLAYLIST" "$PLAYLIST"
    else
        toM3U "$DEVICE_MIRROR/$PLAYLIST" "$PLAYLIST"
    fi
done

rm -rf "$DEVICE_MIRROR/MUSIC/cache"
IFS="$INIT_IFS"

# From Sujee Maniyam's script (http://sujee.net):
#     first copy the files
#     timestamps to be accurate within a second.  This is needed as Unix file
#     system has more accurate timestamps the VFAT file sytem of sansa
if [ "$PLAYLISTS" ]
then
    echo "Copying files to device..."
    rsync -trLv  --modify-window=1 "$DEVICE_MIRROR/MUSIC" \
        "$SANSA_MOUNT"

    # Only try to sync the PLAYLISTS folder if it exists.
    if [ -d "$DEVICE_MIRROR/PLAYLISTS" ]
    then
        rsync -trLv  --modify-window=1 "$DEVICE_MIRROR/PLAYLISTS" \
            "$SANSA_MOUNT"
    fi
fi
echo "Done."
) | zenity --title "Status" --width 500 --height 450 --text-info
```

I only changed the options for rsync.  Should the playlist work with existing music?  Or does everything need to be done on a fresh sync?

On a side note, you wouldn't happen to know why Rhythmbox converts .wma files to .ogg format, would you?

---

### Post by GMWeezel on 2010-01-18
Hm looking at the output of things, it appears the script works correctly. Everything does need to be done on a fresh sync -- the program can only make playlists from the files contained in your Rhythmbox database. It ignores anything that is already on the device and starts fresh. For that reason, I have music that I don't want in a particular playlist in a humongous playlist called "Sansa Master Library" so that the files are still copied to my device. You select the Rhythmbox playlists you want to synchronize and then it puts only the songs in the selected playlist on the Sansa. The reason I have the delete option is because if you were to change your playlists and a certain song was no longer in any of them, you would end up having extra songs on your device that you never listened to.

Try making a playlist in Rhythmbox that contains some songs and runnin the program again and checking the device to make sure the playlist was copied and functions properly (You can still leave the --delete option of rsync at this point). If it copies properly, inside of Rhythmbox, make a playlist that contains all the songs on your device and then synchronize that master playlist in addition to the other ones you would like.

Now, if you have a bunch of songs, the above would probably be a tedious process and I can't think of a _decent_ way to go about doing the above.

---

### Post by trikster_x on 2010-01-18
Thanks for the help with trying to get this to work for me, but it is refusing to put anything more than the .M3U file on my device.  

I can't really use rhythmbox until I find a solution to the whole .ogg file conversion issue, though, since about a third of the files I am trying to sync are .wma format and the clip does not support the .ogg format that rhythmbox converts them to.

Thanks again, and maybe I'll try playing with it some more if the conversion issue goes away.

---

### Post by GMWeezel on 2010-01-18
I'm really interested in figuring out the problem if you'll bear with me a bit. I'll write a debugging version of the script that will dump all the variables to a file tonight.

On another note, I thought OGG was supported when FLAC support was released. Wikipedia seems to support this. Maybe you need to update your firmware?

> Firmware version 01.01.29[12], released in May 2008, enabled Ogg Vorbis compatibility for the Sansa Clip. The 01.01.30 firmware update improved OGG support and added FLAC support. The latest firmware packages for the Sansa Clip are 01.01.32 and 02.01.32, which depend on the hardware revision[13].

---

### Post by trikster_x on 2010-01-20
Yeah, my firmware is the problem with the Clip.  I'll update it ASAP and see if that solves the problem.  Thanks for the info.  Whenever you get the chance to make the debug script, I will be more than happy to run it. 

Thanks again.

Okay, just updated firmware to most current and ogg files still do not play.  I think it is because of the way that rhythmbox converts the files.  I will still run the debug script if you would like.  It would be nice to have a couple small playlists at least.

---

### Post by mawxcarroll on 2010-01-21
Hi GMWeezel,
  I tried your script and it seemed to work, but no songs actually show up on the sansa c250 v2 yet.  Here's what I did:

1) modified script very slightly to account for new rhythmbox directory ~/.local/share/rhythmbox

2) made some playlists and connected the c250

3) connected fine, ran the script

4) everything seems to copy ok: all of the files show up both in rhythmbox and in the file browser

5) disconnect c250; no songs show up on device menu

I'm using firmware 1.01.05P, just out of the box.  I'll try updating the firmware and let you know what happens.

Thanks for this...
tom

---

### Post by mawxcarroll on 2010-01-24
I updated to the latest firmware for my sansa c250 v2 and the script now copies files over to the device.  Playlists aren't showing up as such, so I will try running the debug script again. Before updating, the debug script didn't seem to produce any useful output...is there a particular output I should be looking for?

thanks!
tom

---

### Post by GMWeezel on 2010-01-24
The script produces a file called "debug" probably in the same folder that you ran the script in.

---

### Post by mo-hog on 2010-09-12
This was absolutely brilliant for me! Thank you so much.

A couple of points, which it would be excellent to see you incorporate:
* I get the following error on every run:
"mv: cannot move `/home/aaron/.sansa-mirror/MUSIC/cache' to a subdirectory of itself, `/home/aaron/.sansa-mirror/MUSIC/cache/cache'"
 but it doesn't seem to break anything.
* RB now stores it's files in ~/.local/share/rhythmbox/, at least on Ubuntu Lucid.
* The major version of my firmware is 1 ("FW: V01.02.31P", so fully updated), but my Fuze only works with your m3u playlists. The PLA format ones appear to work correctly, but the playlists on the Fuze are empty. According to [Wiki]("http://en.wikipedia.org/wiki/Sansa_Fuze"), the Fuze supports m3u and wpl, but PLA files are not mentioned. I can find very little on PLA files at all--what makes you think they are used by the Fuze version 1? I "fixed" this in your script by changing the playlist format variable for version 1 ("PLAYLIST_FORMAT="M3U"").
* The script was failing on songs with an "&", because Rhythmbox xml files have these as "&amp;". I therefore changed your cp line to:
cp -l "${SONG//&amp;/&}" "$DEVICE_MIRROR/MUSIC/$FILENAME"
* My first issue was actually that all my songs are stored on a server that I access over ssh. It works fine in RB, but means that all the <locations> in the xml file are like sftp://mythbuntu@192.168.0.102/home/mythbuntu/Music/FLACed_CDs/Nickelback/Nickelback%20-%20Far%20Away.flac, and were not understood by the script. I can't think how this could be fixed, as you would then need the ssh credentials. At that point it would probably be easier to write an RB plugin. I dealt with it by dragging and dropping from the RB playlists into local folders, exporting .pls playlists, running the attached "filename.py" and then find and replacing %20s with " " (clearly I should have dealt with that in the python script!)

My complete unified diff and altered file are attached.

---

### Post by mo-hog on 2010-09-13
My Fuze (running 1.02.31P) has a PLAYLISTS folder as well as a MUSIC folder. My previous hack of your file put the M3U files into MUSIC. It doesn't actually matter, as the Fuze scans all the folders for playlists. I wanted to have them in PLAYLISTS, as that seems neater.

That required me to change the M3U function to match the sed line of the PLA function (which had a "MUSIC\" in front of each filename), though I needed to add a "..\\" at the beginning as the MUSIC folder is a level up from the PLAYLISTS folder. I also had to change a couple of mv lines and paths to get the playlists into that PLAYLISTS folder.

I've attached my revised .sh, which works brilliantly for my Fuze, but I made my edits with shameless disregard for keeping it working for other players. Hopefully it helps someone.

Perhaps the sh script could figure out whether to put the resulting playlists in PLAYLISTS (and therefore make the other edits) based on whether the Fuze has a PLAYLISTS folder.

I guess that the best solution to all of this is for Rhythmbox to get MTP support going properly (with Playlist support)--there are just too many device (and firmware-version) specific quirks to handle all of them in MSC mode. See:
[https://bugzilla.gnome.org/show_bug.cgi?id=503188](https://bugzilla.gnome.org/show_bug.cgi?id=503188)

---

### Post by GMWeezel on 2010-09-15
Glad I could help. I'm actually a Debian user and our Rhythmbox version is comparatively dated. The error from the "mv" statement is because I did something along the lines of "mv * cache" and "cache" happens to be inside the folder I run the mv statement from so it tries to move cache into itself. I hope you'll continue to post anymore "butchering" you do.

---

### Post by naturenut on 2011-06-23
> **GMWeezel said:**
> I hope you'll continue to post anymore "butchering" you do.

Realize this hasn't been active in a while, but I was trying to use your script (with the butchering that mo-hog did) and all of my playlists showed up as empty on Clip+. Got to looking and the line endings were linux, not MS. I changed the line that refers to unix2dos to flip -m, in the pla section and added a similar line to the m3p section. Worked like a charm. It appears that, without unix2dos available, the function defined isn't working (Ubuntu Natty). Happened to have flip installed and gave it a shot.

Noticed that I get &amp; in titles that should have & but that's no biggie since I can now sync my player with the RhythmBox playlists - woohoo!

Thanks a million for your script - and to mo-hog for 'butchering it'.

---

### Post by GMWeezel on 2011-06-23
No problem. It's nice to see my script being put to use.

---

### Post by saltcushy on 2012-06-02
I want to use script *.m3u to *.pla on Samsung wave I. somehow. Impossible?
I'm preferring  the Banshee

---

### Post by GMWeezel on 2012-06-02
I don't have a Samsung Wave, and I did not design the script for it, so it probably won't work. I also have not updated this in a very long time, and I don't even know if it works with Rhythmbox anymore.

---

### Post by saltcushy on 2012-06-02
Omg :(

---

### Post by bowhat on 2013-01-26
Don't know why there aren't more pointers to this thread. There are so many other threads with people complaining about this issue.

Also works like a peach for android. All I had to do was edit the single line for SANSA_MOUNT.

I made a tiny update just to get rid of the mv issue quoted above.

Thank you to everyone.

p.s. naturenut was your issue particular to Sansa maybe?

---

### Post by saltcushy on 2013-05-03
My path to wave I is /run/usr/$user/gvfs works with this? script only creating m3u, no pla,
a Sujee Maniyam's script?

---

