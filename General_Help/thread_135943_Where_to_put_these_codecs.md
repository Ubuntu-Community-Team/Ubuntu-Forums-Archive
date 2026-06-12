---
title: "Where to put these codecs?"
date: 2006-02-24
forum: General Help
---

### Post by SMeeD on 2006-02-24
Ok I installed Mplayer with Automatix and Im trying to watch shoutcastTV using Mplayer. When I try to play the stream it sits and does nothing so I downloaded the essential codec pack which is sitting on my desktop. I read the readme and i the default place to put the codecs is not there. Where should I put these codecs?

---

### Post by GTvulse on 2006-02-24
```
sudo mkdir -p /usr/lib/codecs
sudo tar essential-codecs.tar.bz2 -C /usr/lib/codecs
sudo ln -s /usr/lib/codecs /usr/lib/win32

```

That'll do. Check the contents of /usr/lib/codecs. If everything got installed into a directory inside it, do
```
cd /usr/lib/codecs/<directory>
sudo mv ./* ../

```

To fix it.

---

### Post by SMeeD on 2006-02-24
I get an error like this when I enter the second command you listed

```
tar: invalid option -- e
Try `tar --help' or `tar --usage' for more information.
```

---

### Post by GTvulse on 2006-02-25
that would be because I forgot to include the necessary modifier flags. If you type 'tar --help' you can find them yourself (and be able to do it 1000000 times in the next 80 years of your life ;-)).

Anyway, the flags you need are '-xzf' if dealing with a tar.gz (tar archive compressed with gzip) file and '-xjf' if dealing with a tar.bz2 (tar archive compressed with bzip2).

---

### Post by SMeeD on 2006-02-25
Now I get this:

```
tar: essential-20050412.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

I also used the name "essential-codecs.tar.bz2" like you posted but I get the same error.

I wish i knew more about this then I wouldnt be so helpless :P

---

### Post by Ramses de Norre on 2006-02-25
```
cd directory_file_is_in
tar -xvzf file_name
```
If you type in first two letters of the file name and then press tab the name will be completed automaticaly and you wont make typo's.

EDIT: this is just for the untar problem, follow the earlier suggestions to copy them to the right dir.

---

### Post by SMeeD on 2006-02-25
The "essential-20050412.tar.bz2" is on my desktop. Im still having troubles with this. I put in the commands in this order and these are the errors i get...

```

eric@ubuntu:~$ sudo mkdir -p /usr/lib/codecs
eric@ubuntu:~$ sudo tar -xjf essential-20050412.tar.bz2 -C /usr/lib/codecs
tar: essential-20050412.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
eric@ubuntu:~$ cd /home/eric/desktop
bash: cd: /home/eric/desktop: No such file or directory

```

That is the directory to thedesktop right? I typed it out as I navigated there, I just dont understand whats going wrong...

Edit* Never mind, I took ownership of the folder and moved them all in there manually like I should have done in the first place. It still gives me an error that says "Cannot find codec matching selected -vo and video format 0x32365056"

---

### Post by GTvulse on 2006-02-26
That's better! At least you now know that the codec is so proprietary that not the mplayer guys don't consider it "essential".  :p 

If you searched in google or vivisimo, you'd find some hints in Czeck and German sites, and discover the answer here: <http://www.debianforum.de/forum/viewtopic.php?p=246287>. If you have a recent copy of Winamp somewhere try copying the NSV decoder libraries...

---

### Post by SMeeD on 2006-02-26
I figured out how to get it working last night and now I feel like an idiot :P

Instead of just trying /usr/lib/codecs I tried /usr/lib/win32 (i think) and it worked fine. It was right under my nose the whole time.

---

### Post by GTvulse on 2006-02-26
Glad to hear that! FYR:

```

sudo tar jxf essential-20050412.tar.bz2 -C /usr/lib
cd /usr/lib
sudo mv essential-20050412 codecs
sudo ln -s codecs win32

```

---

