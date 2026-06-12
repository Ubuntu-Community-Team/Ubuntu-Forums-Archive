---
title: "Unable to read Cyrillic/Russian file names mounting with ext2"
date: 2009-09-06
forum: General Help
---

### Post by Bl4deRunner on 2009-09-06
Hi all, I have the following challenge:

I have to copy files from a HD, from a NAS.
It's formatted ext2.
I can mount the drive perfectly using:
mount -t auto /dev/md0 /media/mynewdriv

But when I scan through the folders, Cyrillic (Russian) filenames are shown as:
_______ _______.doc
~$????? ???????.doc
~$_____ _______.doc
??????? ???????.doc

I can't find a way to mount ext2 as unicode, so what are my options to view these files properly?

---

### Post by Bl4deRunner on 2009-09-07
Bump?

---

### Post by Cato2 on 2009-09-07
Some investigation is needed.  Things to find out include:

- do Unicode characters work in your system generally, i.e. Cyrillic fonts?

- are the filenames wrong in all applications or only some?

- does changing the font used to a known good Unicode font (e.g. Arial Unicode MS) help?

Since UTF-8/Unicode normally works without any setup on Ubuntu, and this hard disk is from a NAS that presumably used Samba to serve Windows clients, my suspicion is that it includes filenames that are non-Unicode but are being interpreted as Unicode (not by the ext2 filesystem code, but by applications).

See [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/unicode.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/unicode.html) for some details from a Samba centric perspective on how to configure Unicode etc.  If your filenames/filesystem are in a pre-UTF8 character set, it's best to convert them - see the convmv tool in particular to do this in-place.  Also, see [http://tldp.org/HOWTO/Unicode-HOWTO.html](http://tldp.org/HOWTO/Unicode-HOWTO.html) - the main Linux Unicode HOWTO.  Rather old but has some good pointers.

Please **back up all your data** before using convmv (ideally with an image backup, e.g. Clonezilla Live CD - otherwise you may lose the files that have odd names if the backup program doesn't like these).  If you do use another program (sbackup is very easy to setup up, just do sudo aptitude install sbackup), please double check that the files with odd characters in the name were backed up OK (do a test restore of a few of them).

---

### Post by Bl4deRunner on 2009-09-07
Hi! Thanks for this great reply!
It gives me something to hold on to.

First some background-info:
These drives come from a 2-drive NAS (DNS-323).
They're formatted ext2 in a JBOD config.
I've mounted them to from my ubuntu-live using mdadm, to rebuild the array (MD0) again, and them mounted this array with [mount -t ext2 /dev/md0 /media/mynewdrive]

While these drives were in my NAS, I could mount them with cifs iocharset=UTF8, and cyrillic characters were no problem.

But mounting these drives directly with ext2, gives me unusable filenames.
Does this put a focus on the solution?

By the way: How can you mount ext2 as utf8? afaik, it can't be done with ext2.

---

### Post by Cato2 on 2009-09-08
ext2 and ext3 don't care at all about filename encodings, unlike NTFS which uses a superset of UTF-16 (basically Unicode as 1 or more 16-bit words, whereas UTF-8 is 1 or more 8-bit bytes).  Generally UTF-8 is used as a network format and by Samba/SMB, while Mac HFS+ uses a weirdly normalized variant of UTF-16 I think.

All 'native' Linux filesystems (i.e. not VFAT, NTFS, HFS+, etc) can use UTF-8 or any other filename encoding - it's completely up to the applications using the filesystem.

You don't need to mount ext2 as utf8, as it simply passes the bytes through.  There are a few possibilities:

1. your filenames are corrupted (hence you should do a backup first from a system or live CD that can see the correct filenames, or an image backup).  Or simply mount the filesystem read-only (see 'man mount') to protect it.

2. the application (e.g. terminal, ls, etc) doesn't know the filenames are utf8 encoded - see HOWTOs on locale setup, e.g. [http://lists.debian.org/debian-user/2004/06/msg00243.html](http://lists.debian.org/debian-user/2004/06/msg00243.html)

3. the application is using a font that doesn't include Cyrillic characters for the Unicode codepoints (character values) used in the utf8 filenames

Please answer every one of my other questions, they will help diagnose what's happening here.  

One question: which types of clients originally created the files on the NAS - Windows, Mac, Linux?  

Also, the output of the following commands would be useful

1. mount

2. ls (on a directory with these files)

3. ls >/tmp/test.txt; file /tmp/test.txt

The last one will say what encoding you actually have.

---

### Post by Bl4deRunner on 2009-09-08
Thnx for your time, Cato.
This is as much as I can tell from my work, tonight I can tell you more when I'm behind my system:

These files were created either using Ubuntu 8.10 through a mounted NAS using cifs & iocharset=UTF8, or Windows XP.
It's hard to tell now which system created what file, since we use both systems simultaneously at home.

Right now I'm using Ubuntu 9.04 Live (on USB) to recover these files & put them on my NAS (DNS-323 with new harddrives).

To view the files I use Nautilus & Terminal, Nautilus supports Cyrillic(utf8) for sure, and both show the same filenames:

??????? ???????.doc
_______ _______.doc
~$????? ???????.doc
~$_____ _______.doc

Where I have to note that, after opening these files appear to be identical:
_______ _______.doc
??????? ???????.doc

I didn't check:
~$????? ???????.doc
~$_____ _______.doc
But I guess these files are left after a crashed OpenOffice session.

I'll post the results to your questions when I'm at home.

---

### Post by Bl4deRunner on 2009-09-08
1) mount
```
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//192.168.0.2/Volume_2 on /media/nas2 type cifs (rw,mand)
//192.168.0.2/Volume_1 on /media/nas1 type cifs (rw,mand)
/dev/md0 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
```
2)ls
```
~$_____ _______.doc  _______ __ ______.doc  ??????? ?? ??????.doc  Vyazanie - model platjev.doc
~$????? ???????.doc  _______ _______.doc    ??????? ???????.doc
```
3)ls >/tmp/test.txt; file /tmp/test.txt
```
/tmp/test.txt: ASCII text
```

Does it help?

---

### Post by Cato2 on 2009-09-09
Thanks for that - the last one is interesting as it implies any high-bit characters (8th bit set) are being lost completely somewhere.

Can you also answer these questions from an earlier post?

- do Unicode characters work in your system generally, i.e. Cyrillic fonts?

- are the filenames wrong in all applications or only some?

- does changing the font used to a known good Unicode font (e.g. Arial Unicode MS) help?

I think the key thing is to understand which character encodings (UTF-8, KOI8-R, ISO-8859-x, CP85x - aka Windows codepage) is used by these files.  It may well vary between different directories and files, depending on the client and how it mounted the Samba volume on the NAS.

Experimenting with different locales (at the level of your terminal, so ls will pick this up) is the best thing to try in my view.

What's your current locale?  Look in output of 'env' for LANG, LC_*, etc.

To add a new locale in Ubuntu, try (use whatever local makes sense for you, and check it exists in Ubuntu, see 2nd step):

1. sudo locale-gen de_DE@euro

2. A list of possible values (instead of de_de@euro) can be looked up in the file /usr/share/i18n/SUPPORTED.

3. Then sudo dpkg-reconfigure locales 

4. Then test with ls, less, etc.  Also try Nautilus perhaps.

---

### Post by Bl4deRunner on 2009-09-09
*- do Unicode characters work in your system generally, i.e. Cyrillic fonts?* 
Yes, I can manually rename the files with Cyrillic letters. And it shows properly in Nautilus as in the terminal.

*- are the filenames wrong in all applications or only some?*
All applications I use show the same, when I "browse" for these files. Cyrillic font's isn't a problem anywhere in Ubuntu 9.04.
And I ~could~ access these files properly when the disks were in a NAS mounted through cifs & iocharset=utf8. But now, when mounting the drives directly through mdadmin & mount ext2, it's unreadable.

I just discovered that it isn't only Cyrillic font's:
I had a folder with the name Niña Pastori, but now it shows Ni?a Pastori. :shock:

*- does changing the font used to a known good Unicode font (e.g. Arial Unicode MS) help?*
Well, standard Ubuntu fonts work fine showing Cyrillic and other special fonts. It's just the files on this mounted harddrive...

Through Ubuntu settings I've already added Russian language support. I'll try the other suggestions later when I'm at home again.

I'm suspecting D-Link did something funny with their firmware to support cyrillic font's, because it wasn't supported initially.

---

### Post by Cato2 on 2009-09-09
See [http://www.j3e.de/linux/convmv/man/](http://www.j3e.de/linux/convmv/man/) - this is a very useful tool to migrate filenames from one encoding to another, but please  back up first!  It has an interactive mode so you can see if it makes sense.

In particular, see the section on Samba at the end - this may be what has happened, e.g. the client is working as utf8 on the wire but Samba is doing (perhaps) CP850 or some other single-byte character set in the filesystem.  Once the disk is not accessed via Samba you get these issues.

For the 'Niña Pastori' folder, can you do this and show the results?

ls Ni*astori | od -c -td1

This may help establish what character set is in use, but most likely you have >1 single byte character sets - e.g. ISO-8859-1 for this one, and CP1251 for the Cyrillic filenames (see [http://www.fingertipsoft.com/ref/cyrillic/cp1251.html](http://www.fingertipsoft.com/ref/cyrillic/cp1251.html) )

Doing this for a Cyrillic filename would be good, as long as you can paste in the 'real' filename in UTF8 here.

See also [http://ubuntuforums.org/showthread.php?t=123350](http://ubuntuforums.org/showthread.php?t=123350) - not very relevant but people in that thread had similar problems I think.

---

### Post by Bl4deRunner on 2009-09-09
You're amazing!
:-)
I'll try first thing when I'm at home.

---

### Post by Bl4deRunner on 2009-09-09
Back again:
*ls Ni*astori | od -c -td1*
0000000   N   i 361   a       P   a   s   t   o   r   i   :  \n   (   2
          78  105  -15   97   32   80   97  115  116  111  114  105   58   10   40   50
0000020   0   0   2   )       M   a   r 355   a  \n  \n   N   i   n   a
          48   48   50   41   32   77   97  114  -19   97   10   10   78  105  110   97
0000040       P   a   s   t   o   r   i   :  \n   N   o   .   H   a   y
          32   80   97  115  116  111  114  105   58   10   78  111   46   72   97  121
0000060       Q   u   i   n   t   o       M   a   l   o  \n
          32   81  117  105  110  116  111   32   77   97  108  111   10
0000075

What am I looking at?
Nautilus shows (invalid encoding) under dir/filename.

---

### Post by Bl4deRunner on 2009-09-09
convmv -f cp1251 -t utf-8 -r --exec "echo #1 should be renamed to #2" .
convmv -f ascii -t utf-8 -r --exec "echo #1 should be renamed to #2" .
convmv -f iso-8859-1 -t utf-8 -r --exec "echo #1 should be renamed to #2" .

these don't seem to work:
echo Ni\&#65533;a\ Pastori should be renamed to Ni\&#65533;\&#65533;a\ Pastori

I do get this message:
Your Perl version has fleas #37757 #49830, but Perl is up-to-date.

---

### Post by Bl4deRunner on 2009-09-09
I guess the Cyrillic filenames can't be recovered, I found this thread with people who had the same problem. This got confirmed after I accidentally stumbled upon a recently created Russian document that displayed Cyrillic characters just fine:
[http://forum.dsmg600.info/t651-problem-with-german-characters-mapping-when-mounting-from-linux.html]("http://forum.dsmg600.info/t651-problem-with-german-characters-mapping-when-mounting-from-linux.html")

But the "invalid encoding" problem with filenames like "Niña Pastori" remains. Any clue what the original codepage could be?

---

### Post by Bl4deRunner on 2009-09-10
What I found:
[I]N	i	361	a
78	105	-15	97[/I]

Number 361 coincides with the octal code of ñ considering the Windows Code Page 1252:
[I]Microsoft Windows Code Page 1252
char dec col/row oct hex  description
[ñ]  241  15/01  361  F1  SMALL LETTER n WITH TILDE[/I]

But even though the following command had the wrong codepage, it should have given the Russian "c" instead of another &#65533;:
[I]convmv -f cp1251 -t utf-8 -r --exec "echo #1 should be renamed to #2" .
echo Ni\&#65533;a\ Pastori should be renamed to Ni\&#65533;\&#65533;a\ Pastori[/I]

And if I manually enter a ñ the terminal, it shows the character properly.
If I rename the file manually it's also shown properly in the terminal.

What am I missing? And what's up with the [-15] ascii-code for [ñ] (oct 361)?

---

### Post by Cato2 on 2009-09-10
This is good news actually.  The key next step is to work out the character encoding used for your Cyrillic filenames.

As you have worked out, Niña Pastori filename is encoded in ISO-8859-1 (or something very close - the Windows variant of this uses a few characters you would never use in a filename):

0000000 N i 361 a P a s t o r i : \n ( 2

See position 361 (decimal due to the -td1 in od argument) in [http://en.wikipedia.org/wiki/ISO/IEC_8859-1#Codepage_layout](http://en.wikipedia.org/wiki/ISO/IEC_8859-1#Codepage_layout) - this is the ñ character.

Convmv looks like it is correctly translating this filename into UTF-8 i.e. from 1 to 2 bytes as seen here.  So, please redirect output of convmv into a file for (1) this file, and a file with some cyrillic characters in the name(and please tell me what they are meant to be if possible).  

Then you can look at this with gedit, or Firefox on your local system (change the Firefox character encoding to utf8 and others to see what they say).

Please also paste the convmv output file as follows:

- use pastehtml.com via this script: [http://code.google.com/p/pastehtml/](http://code.google.com/p/pastehtml/) - do something like  "convmv .... | sh pastehtml.sh" 

- it gives you a URL which you can check with Firefox (be sure to set your character encoding as appropriate - e.g. ISO 8859-1 for the Nina name (an example I just did is [http://pastehtml.com/view/090910saJ08OSD.txt](http://pastehtml.com/view/090910saJ08OSD.txt) which contains Niña in ISO-8859-1)

- paste the URL here along with the exact command that generated the output

This avoids the whole issue of the forum software translating character encodings.

Are you absolutely sure that your locale and fonts in the Terminal program support UTF-8?  Type 'locale' in the terminal, and also try saving an HTML file from Firefox that you know has Cyrillic utf8 characters (yahoo.ru or something) and then viewing that with lynx (apt-get install lynx if needed).

The pastehtml test above will help a lot, as it's much easier to tell Firefox to use a specific character encoding than with some other programs.

Also I hear that ROXfiler is good at showing filenames in non-UTF8 character sets - apt-get install rox-filer and give it a go.  See [http://ubuntuforums.org/showthread.php?t=144297](http://ubuntuforums.org/showthread.php?t=144297) for tips on this, convmv, etc.  Even though the statement that NTFS uses CP850 is wrong (NTFS uses Unicode according to Microsoft's internationalisation guru: [http://blogs.msdn.com/michkap/archive/2006/09/24/769540.aspx](http://blogs.msdn.com/michkap/archive/2006/09/24/769540.aspx)), there are many good tips on this thread.

This is quite painful to debug, but once you are on UTF-8 it's MUCH easier... everything remains in a single character set including Cyrillic characters, Spanish accented characters, etc.

---

### Post by Cato2 on 2009-09-10
Responding to your question about the '-15' encoding for Nina file: the reason for this is that you have **multiple character encodings** for the filenames on your disk.  Anyone using the filename for a file must know the character encoding (e.g. ISO-8859-1) to make sense of it.

Not quite sure how this happened since Samba was apparently using utf8, but I suspect that Samba wasn't doing utf8 at all, and was simply passing through the unmodified 8-bit character sets used by the client PCs (e.g. ISO-8859-1 or -15 for the Nina filenames, and Windows-1251 [or something else] for the Cyrillic filenames).

Anyway - the hard part is not doing the conversion, it's identifying which are the character sets.  We know that it's ISO-8859-1 for the Nina type files (presumably MP3 files?) - note that ISO-8859-15 is almost the same, basically just adding the Euro character.  What we don't know is the character set (i.e. encoding basically) for the Cyrillic filenames.

Once you are using UTF-8, at least all this will be in the past, but the trick is to identify which character encodings were used for which files and do a selective convmv to rename them.  

If you have any accented/Cyrillic filenames in archive files (backups, .tar.gz files, etc) you would also need to unpack those, convmv to rename, and repack them.

This is somewhat error prone hence my encouragements to do a backup first, using an image backup (CloneZilla) so that you can reconstruct the exact state of the filesystem.  If the filenames are messed up badly, it's almost as bad as losing the files...

Also, a JBOD system is quite vulnerable to disk errors anyway - RAID-1 or simply 2 separate filesystems would be better.  If you really want 1 big filesystem, look into LVM - however, disabling write caching (hdparm -W0 /dev/sdX) is strongly recommended for integrity with LVM and ext3, and possibly ext2.

---

### Post by Bl4deRunner on 2009-09-10
Well...
I've found this, and the Nautilus-script is a big help.
[http://ubuntuforums.org/showthread.php?t=144297]("http://ubuntuforums.org/showthread.php?t=144297")
BUT!
You really have to double-check the encodings before applying the scripts.

Moreover, I found out that the --exec "echo #1 #2" of convmv doesn't show what the end-result will be. For example:

convmv -f cp1252 -t utf-8 -r --exec "echo #1 should be renamed to #2" .
gave:
echo Ni\&#65533;a\ Pastori should be renamed to Ni\&#65533;\&#65533;a\ Pastori

But 

convmv -f cp1252 -t utf-8 -r --notest .
translated the files properly to:
Niña Pastori

But now I've found other files with different encodings.
What's the easiest way to find the codepage if you know the character & character code?

For the record:
ubuntu@ubuntu:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

---

### Post by StuartN on 2009-09-10
> **Bl4deRunner said:**
> _______ _______.doc
~$????? ???????.doc
~$_____ _______.doc
??????? ???????.doc

One possibility you should consider is whether these files were ever migrated from FAT or NTFS, or some other FS. If so then it is possible that the partition has been correctly mounted already.

---

### Post by Cato2 on 2009-09-11
> **Bl4deRunner said:**
> Well...
...
You really have to double-check the encodings before applying the scripts.

Moreover, I found out that the --exec "echo #1 #2" of convmv doesn't show what the end-result will be. For example:

convmv -f cp1252 -t utf-8 -r --exec "echo #1 should be renamed to #2" .
gave:
echo Ni\&#65533;a\ Pastori should be renamed to Ni\&#65533;\&#65533;a\ Pastori

But 

convmv -f cp1252 -t utf-8 -r --notest .
translated the files properly to:
Niña Pastori

But now I've found other files with different encodings.
What's the easiest way to find the codepage if you know the character & character code?

The reason convmv doesn't appear to work is that your console UTF8 setup is incorrect - either it's not using UTF-8, or more likely the Unicode font used in console doesn't include Cyrillic characters.  Try Arial Unicode MS, which is available in Windows/Office and can be installed in Ubuntu if you don't have it.

If you had uploaded the convmv output to pastehtml.com I could tell you this definitely, and this is also the ONLY way to figure out this character set.

Once we have the actual character values in a file, it's a lot easier to use Firefox to try different character encodings until one of them makes sense, as mentioned above, or to look in web pages documenting character sets (much more work).

This will go much quicker if you respond to my previous post specifically, i.e. run ```
convmv -f cp1252 -t utf-8 -r --exec "echo #1 should be renamed to #2" >convmv.txt
```

Then upload this file to [http://pastehtml.com](http://pastehtml.com) by installing the pastehtml.sh file as mentioned, and then running ```
cat convmv.log | sh pastehtml.sh
```

This is so I can see the exact character set values.  I don't have time to type in the reasons for these requests but they are designed to help identify the source character set, after which the conversion is quite trivial.

Until we figure out the current character set of the Cyrillic characters, it's like trying to find a lost key in a dark cellar, as we have no idea what value to set for the -f parameter.

There are apparently **18 commonly used Cyrillic encodings** and some specific applications use their own variants... see [http://www.unicodecharacter.com/charsets/cyrillic.html](http://www.unicodecharacter.com/charsets/cyrillic.html).  Also, see [http://www.cs.tut.fi/~jkorpela/chars.html#problems](http://www.cs.tut.fi/~jkorpela/chars.html#problems) for common issues when the character sets don't match.

Try running rox-filer as well, it's much easier to try different character sets with this by simply doing "CHARSET=cp850 rox-filer" etc, and it has special support for viewing filenames in multiple character sets as well as UTF-8.  See [http://ubuntuforums.org/showpost.php?p=801598&postcount=5](http://ubuntuforums.org/showpost.php?p=801598&postcount=5)

---

### Post by Bl4deRunner on 2009-09-11
Thanks for all the useful info, Cato2! I've learned a lot.
I actually managed to change most file names correctly to UTF8, switching through different code-pages, so there's a big relief there.
the -i (interactive mode) for convmv was a necessity.
Some filenames are still a mistery though, so I'll follow your tip & answer tomorrow.
Thanks for helping me! How come you know so much about this?

---

### Post by Cato2 on 2009-09-11
> **StuartN said:**
> One possibility you should consider is whether these files were ever migrated from FAT or NTFS, or some other FS. If so then it is possible that the partition has been correctly mounted already.

That's worth thinking about, but what's really needed is to figure out the character set the filenames are using.  Also, I've established that ext2/ext3 doesn't require a 'mount as utf8' option (and in fact doesn't have one) - it doesn't restrict the character encoding of the filenames, so whatever encoding was used to create the filename is what you get.  (JFS doesn't work like this though, it mandates utf8).

---

### Post by Cato2 on 2009-09-11
Glad this is getting sorted.  In a former life I used to develop internationalisation features (particularly character encoding support) for a web application, which is how I know this stuff.

---

