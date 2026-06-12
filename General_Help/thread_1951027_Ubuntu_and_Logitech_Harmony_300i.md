---
title: "Ubuntu and Logitech Harmony 300i"
date: 2012-04-01
forum: General Help
---

### Post by thedemon13666 on 2012-04-01
Hello,
I am currently trying to set up my logitech harmony 300i with ubuntu 11.10 x64 however when running congruity it fails to detect the remote (I have been on the harmony website and downloaded the file which opens congruity)

Is it possible to set this remote up on ubuntu?

---

### Post by thedemon13666 on 2012-04-02
bump

---

### Post by dave2001 on 2012-04-02
Have you tried any of the stuff in this thread?

[http://ubuntuforums.org/showthread.php?t=1704890](http://ubuntuforums.org/showthread.php?t=1704890)

There are a few other possible threads with answers too. Searching the forums to see if your question has already been answered is always a good start.

Let us know if none of them help though!

---

### Post by thedemon13666 on 2012-04-03
Thanks for the help,

The problem is that congruity is not detecting my remote, I am sure I have read somewhere that the logitech harmony 300i has problems being programmed under linux.

Would the remote work in ubuntu if I programmed it in windows (I dual boot)?

---

### Post by dave2001 on 2012-04-03
For the first several months I had a Harmony 300, I had trouble getting Windows7 to recognize it, and Windows is one of the "officially" supported OS's. The problem was fixed after a harmony software update.

I guess what I'm trying to say is this:
It can be a headache to get some commercial software working right when integrating it with open source. If you have the option of doing it on Windows (since your dual-booting), you'll probably save yourself some time by doing it that way. If your trying to get things working in Linux just for the principle, kudos, but I don't have much helpful advice.

Also, I doubt setting the remote up in Windows will affect how the remote is recognized (or not) by Ubuntu.

The only suggestions I have for Ubuntu is to try running congruity as root, and to look into the program's config files to see if there's anything that can be changed to help.

Are you getting any kind of error messages when your remote isn't recognized properly? If you are post it here, and maybe someone more knowledgeable than me will take a look.

---

### Post by thedemon13666 on 2012-04-04
Here is the error I get:

Unknown error
    (libconcord function get_identity error 1)

Traceback (most recent call last):
  File "/usr/local/bin/congruity", line 521, in _WorkerFunction
    False
  File "/usr/local/bin/congruity", line 137, in worker_body_connect
    None
  File "/usr/local/lib/python2.6/dist-packages/libconcord.py", line 97, in __call__
    raise LibConcordException(self.func_name, result)
LibConcordException: libconcord function 'get_identity' failed with error code 1 ('Unknown error')


I think my main concern now is whether programming the device in windows means that it only operates in windows, if this is not the case then I will just program using windows.
I can't right this second as I am not at home.
Bit annoying as the 300 doesnt seem to have had much use anywhere...

---

### Post by artistgay on 2012-06-19
i am getting the following error in ubuntu 12.04:
Failure
Commandline error
see below for details
Error: precisely one filename argument is required
Traceback (most recent call last):
File "usr/bin/congruity", line 1945, in main
raise CmdLineException ....

---

### Post by revnoah on 2013-01-13
I got this same error, and that's all the program does. If you have access to a supported Windows machine, I highly recommend using the official software. Your settings are stored online so you're not dependent on any particular PC to set up the device.

> **artistgay said:**
> i am getting the following error in ubuntu 12.04:
Failure
Commandline error
see below for details
Error: precisely one filename argument is required
Traceback (most recent call last):
File "usr/bin/congruity", line 1945, in main
raise CmdLineException ....

---

### Post by Robbyx on 2013-04-13
For the record:

Make sure congruity, concordance and its dependencies are installed. Do not run concordance as a stand alone. 

User browser to login to  [http://members.harmonyremote.com](http://members.harmonyremote.com). Set up a device  in the site to test.

When the browser says open/ save choose: open with congruity  ;follow instructions.

I had problems with firefox showing the file saving option. Opera worked ok and congruity opened the file correctly.

---

### Post by swt2c on 2014-04-04
Harmony 300 is now supported using mhgui (part of congruity).

---

### Post by oldos2er on 2014-04-05
Old thread closed.

---

