---
title: "mencoder no such file even though it is installed?"
date: 2009-11-10
forum: General Help
---

### Post by sdowney717 on 2009-11-10
found it here why is this a problem

scott@scott-desktop:/usr/bin$ ./mencoder
MEncoder SVN-r29375-4.4.1 (C) 2000-2009 MPlayer Team
No file given

Exiting... (error parsing command line)
scott@scott-desktop:/usr/bin$ 



wanted to change some video formats but mencoder is not working?
> scott@scott-desktop:~/Videos$ sudo apt-get install mencoder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mplayer-doc
The following NEW packages will be installed:
  mencoder
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,672kB of archives.
After this operation, 3,797kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  mencoder
Install these packages without verification [y/N]? y
Selecting previously deselected package mencoder.
(Reading database ... 175294 files and directories currently installed.)
Unpacking mencoder (from .../mencoder_2%3a1.0~rc3+svn20090620~karmic~ppa4_i386.deb) ...
Processing triggers for man-db ...
Setting up mencoder (2:1.0~rc3+svn20090620~karmic~ppa4) ...
scott@scott-desktop:~/Videos$ mencoder
bash: /usr/local/bin/mencoder: No such file or directory
scott@scott-desktop:~/Videos$ 


---

### Post by lloyd_b on 2009-11-10
At a guess, at one time you had a manually compiled version of mencoder on the machine.  This bug is probably some residual from that.> scott@scott-desktop:/usr/bin$ ./mencoder
MEncoder SVN-r29375-4.4.1 (C) 2000-2009 MPlayer TeamFrom this, you have mencoder installed (from the repos) in /usr/bin.> scott@scott-desktop:~/Videos$ mencoder
bash: /usr/local/bin/mencoder: No such file or directorybut when you try to run 'mencoder', it's attempting to execute it from /usr/**local**/bin.

If you look in '/usr/local/bin', you'll probably find a "broken symlink" (a symlink to a file that doesn't exist) named 'mencoder'.  When you attempt to execute such a symlink, you get the "...No such file or directory" message.  Because '/usr/local/bin' precedes '/usr/bin' in your PATH, when you just type 'mencoder', it looks in '/usr/local/bin' first, finds the symlink, and attempts to execute it, resulting in the error.

If you delete that symlink from '/usr/local/bin', mencoder should work.

Lloyd B.

---

### Post by sdowney717 on 2009-11-10
makes sense, but
there is nothing in there named mencoder
usr/bin does have mencoder

actually i would like to compile mencoder with mp3 support, do you know hoe to do this?

---

### Post by lloyd_b on 2009-11-10
Hmmm - *something* is telling it to run /usr/local/bin/mencoder...

In a terminal window, type "which mencoder" and make sure that it's pointing to "/usr/bin/mencoder".  It may be something somewhere else that's intercepting the 'mencoder' command and pointing it towards /usr/local/bin.

Lloyd B.

---

### Post by sdowney717 on 2009-11-10
i can force it to run in my home directory by copying it and using ./mencoder

scott@scott-desktop:~/Videos$ which mencoder
/usr/bin/mencoder
scott@scott-desktop:~/Videos$ mencoder
bash: /usr/local/bin/mencoder: No such file or directory
scott@scott-desktop:~/Videos$

---

### Post by lloyd_b on 2009-11-10
> **sdowney717 said:**
> i can force it to run in my home directory by copying it and using ./mencoder

scott@scott-desktop:~/Videos$ which mencoder
/usr/bin/mencoder
scott@scott-desktop:~/Videos$ mencoder
bash: /usr/local/bin/mencoder: No such file or directory
scott@scott-desktop:~/Videos$

Or just type "/usr/bin/mencoder", which should explictly force it to run the 'mencoder' in the "/usr/bin" directory.

I do NOT understand this - the "which" command should tell you precisely what is being run if you type "mencoder".  What is telling it to run "/usr/local/bin/mencoder"?:confused:

Lloyd B.

Edit: Just for sanity's sake, I did "sudo apt-get install mencoder" on my machine.  It works fine, so whatever is going on is specific to your machine...

---

### Post by 3rdalbum on 2009-11-10
> **sdowney717 said:**
> found it here why is this a problem

scott@scott-desktop:/usr/bin$ ./mencoder
MEncoder SVN-r29375-4.4.1 (C) 2000-2009 MPlayer Team
No file given

Exiting... (error parsing command line)

Mencoder is a command-line program, and you didn't give it any details of what you want to do. I'd highly suggest you find a GUI frontend for Mencoder, that will give you a simple point-and-click interface for using Mencoder.

I'm pretty sure Mencoder from the Ubuntu repositories should have MP3 support. If it doesn't, you might need to install the "unstripped" versions of the libav pckages (this can be done from Synaptic).

---

### Post by sdowney717 on 2009-11-10
looks like it is using unstripped already?

the mencoder line i would like to use is this

./mencoder test.mpg -o output.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=2:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac mp3lame -lameopts cbr:br=128

this one just copies the audio portion. But my media player when i try to play this i get a short hiss and then silence

./mencoder test.mpg -o output.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=2:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac copy

> scott@scott-desktop:~/Videos$ ./mencoder test.mpg -o output.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=2:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac mp3lame cbr:br=128
MEncoder SVN-r29375-4.4.1 (C) 2000-2009 MPlayer Team
MPlayer was compiled without libmp3lame support.
scott@scott-desktop:~/Videos$ 


---

### Post by sdowney717 on 2009-11-10
[http://forums.buyscripts.in/installation-support/2436-mplayer-compiled-without-libmp3lame-support-please-help.html](http://forums.buyscripts.in/installation-support/2436-mplayer-compiled-without-libmp3lame-support-please-help.html)

think this will work to compile mplayer with mp3 support?

Installation:

cd /usr/local/src/lame-3.97
./configure --prefix=/usr
make && make install

cd /usr/local/src/mplayer
./configure --codecsdir=/usr/local/lib/codecs --extraincdir=/usr/local/src/lame-3.97 --extralibdir=/usr/local/lib --prefix=/usr/local
make && make install


Got it to work by compiling it and it now runs like it should
[http://ubuntuforums.org/showthread.php?p=8287073#post8287073](http://ubuntuforums.org/showthread.php?p=8287073#post8287073)

---

