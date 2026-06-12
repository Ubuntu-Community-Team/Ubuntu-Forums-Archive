---
title: "Install MS-DOS in DOSEMU"
date: 2010-04-22
forum: General Help
---

### Post by thefish123 on 2010-04-22
Hi everyone,

I have been playing (I say “playing” because I have no real business reason to be doing this) with DOSEMU and getting my vintage copy of WordPerfect 5.1 running.

I have got it running and it works GREAT.  I am running DOSEMU on the console for the most part as this is the closest experience I can get to good old-fashioned DOS.  Most DOS apps look right running on the console.  I am very impressed.  I have a couple of questions however.

When I start DOSEMU using the -s parameter (on the console) I do not get access to my mouse.  When I prefix it with sudo I do.  Does starting DOSEMU with -s not elevate to the same “level” as running it with sudo?

$ dosemu -s     <--- no mouse
$ sudo dosemu -s      <--- this gets me the mouse

Is there some way I can force DOSEMU to request full elevation everytime I start it on the console?  Pr every time I start it period?  Or should I just keep using sudo?

I have even installed Windows 3.1 inside DOSEMU and this works well too in VGA mode.  It seems to break in SVGA mode when using the Trident drivers recommended here [http://www.dosemu.org/docs/README/1.4/windows.html#AEN666](http://www.dosemu.org/docs/README/1.4/windows.html#AEN666)

Finaly, how can I install my copy of MS-DOS 6.22 inside DOSEMU?  I have it on original floppies (no floppy drive on my laptop), in VirtualPC floppy disk format and in folders containing the files found on each disk.

Best regards,
The Fish.

---

### Post by thefish123 on 2010-05-04
Does anyone know how (or if it’s even possible) to install MS-DOS inside DOSEMU using folders containing the content of the diskettes?  I also have VFD-style (created by VirtualPC 2007) images of the diskettes.

I am trying to recreate my vintage MS-DOS setup complete with WP51, Norton Commander, SideKick and IBM’s most amazing and perfect “MASTMENU”.

Best regards,
The Fish

---

### Post by thefish123 on 2010-05-13
Sorry to keep bumping this thread but I can hardly believe that no one knows how to install MS-DOS inside DOSEMU.  I have looked on the DOSEMU website and it says it's possible (but not necessary).

I don't care that it's not necessary.  I just want to try it for nostalgic reasons...  Any idea if I can do this from folders containing the files found on the original installation diskettes?  Or do I need diskette images?  Or possibly even REAL life floppy disks?

Any suggestions would be appreciated.  Even if I am overlooking something obvious.  Thanks!

Regards,
The Fish

---

### Post by ronnielsen1 on 2010-05-13
I haven't played with dosemu too much but I'm a big fan of dosbox. Have you tried these programs you want to install in dosbox.

I loved dos. I resisted Win 3.11 at first

---

### Post by ronnielsen1 on 2010-05-13
I did find this from a xandros forum

> 1.Install dosemu and xfonts-dosemu using Xandros update 
2.As root create a directory named dos under /var/lib/dosemu 
3.As root using XFM or from the console give everyone the read/write/execute rights to the dos directory. (chmod 777 /var/lib/dosemu/dos) 
4.As a user copy your dos files to /var/lib/dosemu/dos 
5.As root edit /etc/dosemu/dosemu.conf. Find the following lines and modify them as noted. [http://forums.xandros.com/viewtopic.php?t=1094](http://forums.xandros.com/viewtopic.php?t=1094)

Of course, you might have to ubuntuize it

---

### Post by ronnielsen1 on 2010-05-14
Any luck?

---

### Post by emendelson on 2010-05-14
Explained in full here (feel free to ignore the references to WordPerfect):

[http://www.columbia.edu/~em36/wpdos/linux.html#otherdos](http://www.columbia.edu/~em36/wpdos/linux.html#otherdos)

---

### Post by jamillikan on 2010-05-30
Here's how I did it after dosemu was already installed from the repositories and working, but I required a private MSDOS622:

1.  Launch a terminal.
2.  cp /etc/dosemu/dosemu.conf /home/username/dosemu.conf [ENTER]
3.  mv dosemu.conf .dosemurc [ENTER]
4.  cd .dosemu [ENTER]
5.  mkdir dos622 [ENTER]
6.  cd ~ [ENTER]

7.  Download the CD version of msdos622 from the web or use your floppies and copy/paste everything from attrib.exe to xcopy.exe to your /home/username/.dosemu/dos622 folder.

8.  Launch a terminal
9.  gedit .dosemurc [ENTER]
10.  Scroll down to Line 68 (or thereabouts) and find the line that begins $_hdimage = freedos:ro" and place a hashmark (#) in front of it.
11.  Go to the end of the line you placed the hashmark on and press [Enter] to add a new line and type:

$_hdimage = "dos622"

Save and close the file.

cd .dosemu/dos622 [ENTER]

Edit your autoeexec.bat file as follows:

@echo off

path c:\bin;c:\gnu;c:\dosemu;c:\dos622;
set HELPPATH=c:\help

set TEMP=c:\tmp

set BLASTER=A220 I5 D1 H5 T6

prompt $P$G

Save the file changes and exit.

Edit your config.sys file:

dos=umb,high

files=60

lastdrive=z



Save the file changes and edit.

That should be the ticket!  Enjoy.

---

