---
title: "Netatalk (oneric) Cannot Copy .AppeDouble directories"
date: 2011-11-21
forum: General Help
---

### Post by bvz on 2011-11-21
I have a server running 11.10 server.

I installed netatalk via apt (2.2beta~4-1) and am having trouble copying files to the machine from my Mac (which is running OSX Lion).

Some files will copy.  Others just give me an error:

```
The operation can’t be completed because an unexpected error occurred (error code -50).
```


When I drop into the command line and try to copy the entire directory I get errors dealing with the .AppleDouble directory:

```
/Volumes/Media/Music: cp -R ~/Documents/FreeNas\ Backup/music/10,000\ Maniacs/* .
cp: ./Our Time In Eden/.AppleDouble: Invalid argument
cp: /Users/bvz/Documents/FreeNas Backup/music/10,000 Maniacs/Our Time In Eden/.AppleDouble: unable to copy extended attributes to ./Our Time In Eden/.AppleDouble: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/.Parent: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Candy Everybody Wants.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Circle Dream.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Eden.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Few And Far Between.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Gold Rush Brides.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/How You've Grown.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/I'm Not The Man.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/If You Intend.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Jezebel.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Noah's Dove.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Stockton Gala Days.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/These Are Days.mp3: Invalid argument
cp: ./Our Time In Eden/.AppleDouble/Tolerence.mp3: Invalid argument
```


but the actual files copy over correctly.


I cannot manually create an .AppleDouble directory

```
/Volumes/Media/Music: mkdir .AppleDouble
mkdir: .AppleDouble: Invalid argument
```

but perhaps that is just a basic limitation of the command line in OSX.  I don't know.



I am currently working my way through the Netatalk documents, but they are kind of dense (or, rather, I am kind of dense and they are difficult for me to digest).

Can anyone offer any clues as to where I should start looking?

Also, if anyone has a good tutorial on understanding Netatalk (vs. just getting it up and running) I would appreciate that as well.  Thanks!

---

### Post by dcstar on 2011-11-21
Names starting with "." are legal in Linux filesystems, they are not in other filesystems (like NTFS).

---

### Post by bvz on 2011-11-21
> **dcstar said:**
> Names starting with "." are legal in Linux filesystems, they are not in other filesystems (like NTFS).

Thanks for the quick reply.  I may not have explained myself correctly.

I have an Ubuntu server (with ext4 file system on it) running the Netatalk package (2.2~beta 4-1) serving to a couple of Macintosh computers running OS X Lion (with HFS+ formatted drives).

I am unable to properly save files from the Mac to the Ubuntu server because of the issue I described above (I cannot copy or create .AppleDouble files).  There are no Windows machines involved and none of the drives are formatted using NTFS.

Any other ideas?

Thanks.

---

### Post by slowfranklin on 2011-11-21
> **bvz said:**
> ... (I cannot copy or create .AppleDouble files).  ...
Exactly. You can't. So don't.

---

### Post by bvz on 2011-11-21
> **slowfranklin said:**
> Exactly. You can't. So don't.

I'm a little confused by your reply. As far as I understand it (and I am still trying to learn) .AppleDouble directories hold metadata for the actual files in the regular directory.

When I try to copy regular files via the finder (from my Mac to the Ubuntu server) it fails with an error -50.

When I open a terminal on my Mac and try to copy the same directories from the local drive to a mounted volume (mounted from the Ubuntu server, and I am not ssh'ing into the server, but just using the local command line to manage the files on the mounted volume) using cp -R I get the afore-mentioned errors regarding the .AppleDouble directories.  I have no proof, but I suspect that the errors in the terminal and the errors in the Finder are related.

So I am not *actively* trying to copy .AppleDouble directories... they are just coming along for the ride.

Are you telling me that I can't use cp -R from a terminal on my Mac?  If so, how do you manage files on the server if you cannot touch .AppleDouble directories?  Do you think the Finder error is related?

I have tried running sudo dbd -rv on the afp volumes (from the command line on the server) to little avail.  I will try sudo dbd -rfv tonight to see if it improves anything.  

But any insight (with even the tiniest bit of explanation or links) would be greatly appreciated.

---

### Post by bvz on 2011-11-22
I have a theory (but I am not able to test it at the moment)...

The folders I am trying to copy to the Ubuntu server were originally copied FROM a freeNas server.  These folders must have come across with the .AppleDouble directories intact (in fact, I know that these folders have the .AppleDouble directories because I can see them in the terminal).

I'm guessing that these files don't normally live on an HFS+ drive.  So, when I try to copy the directory over to the Ubuntu server, these files (which really should not exist) are included in the copy and at that point Netatalk balks.

So, slowfranklin was dead on (albeit a bit terse) when he/she suggested that I not try to copy the .AppleDouble files.  It just took me a bit of messing about to realize that these files should never even exist on my Mac in the first place and that the issue is a leftover from having brought them over from my old freeNas box.

I'll be able to properly test this tomorrow and then report back.

---

### Post by bvz on 2011-11-22
Theory confirmed.  I spent a few moments carefully deleting the .AppleDouble directories from one of the directory trees that would not properly copy over.  Once that was fixed, I was able to properly copy the files via the finder.

Now I just need to whip up a script to kill them all...

---

### Post by RLovelett on 2012-02-01
cd into the directory above the files not transferring and then execute:

find . -name ".AppleDouble" -type d -exec rm -rf {} \;

Worked for me when I was having the same issue.

---

### Post by Khayyam on 2012-02-01
bvz ..

It sounds like the issue is/was how you have configured the share in AppleVolumes.defaults, is "options:usedots" set? eg:

/etc/netatalk/AppleVolumes.defaults
```
/path/to/share sharename allow:username1,username2 cnidscheme:cdb options:usedots
```These options are explaned in the [Netatalk Manual]("http://netatalk.sourceforge.net/2.0/htmldocs/AppleVolumes.default.5.html")

HTH ..

---

### Post by RLovelett on 2012-02-03
```

# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots

# The "~" below indicates that Home directories are visible by default.
# If you do not wish to have people accessing their Home directories,
# please put a pound sign in front of the tilde or delete it.
~/ "Home Directory" cnidscheme:dbd options:usedots,upriv
~/.TimeMachine "TimeMachine" cnidscheme:dbd options:usedots,upriv,tm

```

This is cut and paste from my settings. I think it is already setup correctly.

---

### Post by Khayyam on 2012-02-04
> **RLovelett said:**
> [...]This is cut and paste from my settings. I think it is already setup correctly.

RLovelett ...

I was asking bvz the question not saying it **should** be set (it is an option after all). In order to troubleshoot the problem I need to know how its setup, and this information wasn't provided by the OP. I perhaps could have been clearer, but by asking the question and linking to the Manual, I assumed that the information relating to that option might be read, and that it might help in understanding why this happened.

The Netatalk Manual: Chapter 5 states:

> 
usedots: Don't do :hex translation for dot files. note: when this                 option gets set, certain file names become illegal. These are                 .Parent and anything that starts with .Apple.

So, if it is set 'dotfiles' will be named correctly (otherwise they will be encoded with a HEX ":2e") BUT certain filenames become illegal, namely ".AppleDouble". Though "usedots" is preferably set, when copying files from a share that Netatalk has already been serving (Netatalk's cnid_meta daemon creates these .AppleDouble files to store CNID metadata) to a share with "usedots" set it will not be able to copy the "illegal filenames". From bvz's code snippit he's copying from "FreeNAS", which I assume was serving these same files via Netatalk (hence the presence of .AppleDouble files), to another share, I assume with "usedots" set, and BINGO.

I'm guessing this is/was the issue, but without knowing if bvz has "usedots" set I can't be sure.

As for your /etc/netatalk/AppleVolumes.default you are nesting volumes (~/.TimeMachine is nested in ~/) this is a no-no for CNID. See the "Note" in [Chapter 3 of the Netatalk Manual]("http://netatalk.sourceforge.net/2.0/htmldocs/configuration.html").

HTH ...

---

