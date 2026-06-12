---
title: "tar package will not unload"
date: 2009-08-20
forum: General Help
---

### Post by Len Tyree on 2009-08-20
a little help please?
downloaded this package from sourceforge; attempting to open/unload/install it, but get the following messages.

len@len-desktop:~$ sudo tar zxvf gdc3play-0.1.tar.gz
tar: gdc3play-0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

the package is there on my desktop, (i can see it) but apparently can't be found??

i am running ubuntu 9.04.

any help would be appreciated.
thanks, len tyreehttp://ubuntuforums.org/images/icons/icon5.gif

---

### Post by tgeer43 on 2009-08-20
I can think of only two reasons. Either:

- You are typing the filename incorrectly.

Or more likely:

-  You are not currently in the correct directory.

Do an 'ls' command and see if your file is listed. If it is then use copy/paste on the listed filename to complete your tar command to eliminate the possibility of a typo.
If it is not listed then cd to your Desktop directory, eg. 'cd ~/Desktop' (or you can just include the full path in your tar command, eg. 'tar zxvf ~/Desktop/gdc3play-0.1.tar.gz')

And why are you using 'sudo' with your tar command? If ***you ***downloaded it and it's in ***your***  /Desktop directory then you should be the owner and 'sudo' is unnecessary.

tgeer

---

### Post by 3rdalbum on 2009-08-20
There's a simple reason:

The terminal shows that it is opened inside your home directory. And you say that the file is on your desktop.

You need to type:

```
cd Desktop
```

in order to navigate to the "Desktop" folder.

You don't need to decompress the archive on the command-line though - just double-click on the archive and decompress it through the File Roller gui.

Also, you might want to install the "nautilus-open-terminal" package. This gives you a right-click-menu-item in your file browser that will open a terminal within the folder that your file browser is in. So you'd open the decompressed folder and then right-click in the window and choose Open In Terminal.

---

### Post by tgeer43 on 2009-08-20
> The terminal shows that it is opened inside your home directory. And you say that the file is on your desktop.Hmm... I thought that's what I said. The only reason that I didn't say it conclusively is that not everyone's command prompt shows their current directory. Some folks change their prompt by editing their ~/.bashrc file.

tgeer

---

