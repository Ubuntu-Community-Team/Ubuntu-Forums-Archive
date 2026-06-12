---
title: "How do I install the official DivX codec in Ubuntu?"
date: 2006-04-08
forum: General Help
---

### Post by Noah0504 on 2006-04-08
DivX Labs has delivered with [DivX 6.1.1 for Linux]("http://labs.divx.com/DivXLinuxCodec").  I was wondering how I can set this up to work with Ubuntu?  Can it work along with Totem or should I install something else like the Helix player?

---

### Post by taurus on 2006-04-08
First, remove the # in front of all the lines that have universe & multiverse in /etc/apt/sources.list.  Then, install w32codecs and you should be all set...

To edit your /etc/apt/sources.list, click on Applications -> Accessories -> Terminal.  Then type
```

sudo gedit /etc/apt/sources.list

```
When you are done, save it and from the prompt, type
```

sudo apt-get update
sudo apt-get install w32codecs

```

---

### Post by Rory on 2006-04-08
I believe he's asking how to install the new DivX codec.  This is what I did.  It looks like it worked but I'm not sure how to actually confirm it.  So, any other posts to help us through and confirm?

1) Download the tar ball from here:[http://download.divx.com/labs/divx611-20060201-gcc4.0.1.tar.gz](http://download.divx.com/labs/divx611-20060201-gcc4.0.1.tar.gz)

2) Extract it to its folder and then go to that folder in terminal.
3) type: sudo ./install.sh
Password: enter your password
4) Press 'Q' (to take you to the end of the user agreement)

Do you accept the terms of this agreement? Please type yes or no.
yes
5) Type 'yes' and hit enter.

```

Proceeding with installation
grep: /etc/ld.so.conf: No such file or directory
Archive:  contents.dat
   creating: /tmp/.divx/include/
   creating: /tmp/.divx/include/common/
  inflating: /tmp/.divx/include/common/DivXPortable.h
  inflating: /tmp/.divx/include/common/FourCC.h
  inflating: /tmp/.divx/include/common/FourCCs.h
  inflating: /tmp/.divx/include/common/FormatInfo.h
   creating: /tmp/.divx/include/encoder/
  inflating: /tmp/.divx/include/encoder/Settings.h
  inflating: /tmp/.divx/include/encoder/EncoderCallback.h
  inflating: /tmp/.divx/include/encoder/FrameResult.h
  inflating: /tmp/.divx/include/encoder/FrameOutput.h
  inflating: /tmp/.divx/include/encoder/EncoderInterface.h
  inflating: /tmp/.divx/include/encoder/FrameInput.h
  inflating: /tmp/.divx/include/encoder/FeedbackInterface.h
  inflating: /tmp/.divx/include/encoder/Cli.h
  inflating: /tmp/.divx/include/encoder/DivXException.h
   creating: /tmp/.divx/include/decoder/
  inflating: /tmp/.divx/include/decoder/LibQDec.h
   creating: /tmp/.divx/lib/
  inflating: /tmp/.divx/lib/libdivx.so

```

Then, you should see libdivx.so here, like this:
```

rory@ubuntu: whereis libdivx.so
libdivx: /usr/local/lib/libdivx.so

```

Now, whether it's now be used by Xine and MPlayer, I have no idea.  But, that's how far I've come, so far.

---

### Post by Sale on 2006-10-10
> **Rory said:**
> I believe he's asking how to install the new DivX codec.  This is what I did.  It looks like it worked but I'm not sure how to actually confirm it.  So, any other posts to help us through and confirm?

1) Download the tar ball from here:[http://download.divx.com/labs/divx611-20060201-gcc4.0.1.tar.gz](http://download.divx.com/labs/divx611-20060201-gcc4.0.1.tar.gz)

2) Extract it to its folder and then go to that folder in terminal.
3) type: sudo ./install.sh

 *****

Then, you should see libdivx.so here, like this:
```

rory@ubuntu: whereis libdivx.so
libdivx: /usr/local/lib/libdivx.so

```

Now, whether it's now be used by Xine and MPlayer, I have no idea.  But, that's how far I've come, so far.

Instalation went well here... :)

However...does anyone know how do I make dvd::rip (transcode) or mencoder actually use the divx codec ?

---

### Post by MetalMusicAddict on 2006-10-10
[HERES]("http://forums.divx.com/forum/forum.php?fid=35") a link to the linux section on their forums.

---

### Post by Dayylin on 2007-05-12
Did all the steps and got this. Look at the last line. Any ideas?

Proceeding with installation
Archive:  contents.dat
   creating: /tmp/.divx/include/
   creating: /tmp/.divx/include/common/
  inflating: /tmp/.divx/include/common/DivXPortable.h  
  inflating: /tmp/.divx/include/common/FourCC.h  
  inflating: /tmp/.divx/include/common/FourCCs.h  
  inflating: /tmp/.divx/include/common/FormatInfo.h  
   creating: /tmp/.divx/include/encoder/
  inflating: /tmp/.divx/include/encoder/Settings.h  
  inflating: /tmp/.divx/include/encoder/EncoderCallback.h  
  inflating: /tmp/.divx/include/encoder/FrameResult.h  
  inflating: /tmp/.divx/include/encoder/FrameOutput.h  
  inflating: /tmp/.divx/include/encoder/EncoderInterface.h  
  inflating: /tmp/.divx/include/encoder/FrameInput.h  
  inflating: /tmp/.divx/include/encoder/FeedbackInterface.h  
  inflating: /tmp/.divx/include/encoder/Cli.h  
  inflating: /tmp/.divx/include/encoder/DivXException.h  
   creating: /tmp/.divx/include/decoder/
  inflating: /tmp/.divx/include/decoder/LibQDec.h  
   creating: /tmp/.divx/lib/
  inflating: /tmp/.divx/lib/libdivx.so  
**cp: cannot stat `/tmp/.divx/include/*.h': No such file or directory**

---

### Post by Nathan.Flow on 2007-06-21
I received the same error, although their are different download able files out their, i forget where i got mine, but i ran the install and still no luck but at least it had no errors. just don't know how to get the codec to work with fire fox.   the name of the file i'm talking about is divx611-20060201-gcc4.0.1.tar.gz
try this web page.
[http://dharshin.freehostia.com/node/2](http://dharshin.freehostia.com/node/2)
or this site
[http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec)
hope this helps you, can any one help me... DivX with Fire Fox, or Swift Fox rather, (same thing if you ask me.)

---

### Post by Carbunkel on 2007-06-22
I got DiVX to work with my computer's media players, but not with my swiftfox. Do I need something else? I'm also pretty new to this Linux stuff, so step by step would be nice if possible lol.

Thanks.

---

### Post by lenninct on 2007-07-09
Just a quick note, make sure that you set your account to root instead of admin  underSystem/Administration/Users and Groups

Just select yoour account and hit properties, then under the Advanced tab, change the Main Group to Root instaed of Admin.

Hope this helps some ppl out there

---

### Post by ARandomKid on 2007-07-11
> **Dayylin said:**
> Did all the steps and got this. Look at the last line. Any ideas?

Proceeding with installation
Archive:  contents.dat
   creating: /tmp/.divx/include/
   creating: /tmp/.divx/include/common/
  inflating: /tmp/.divx/include/common/DivXPortable.h  
  inflating: /tmp/.divx/include/common/FourCC.h  
  inflating: /tmp/.divx/include/common/FourCCs.h  
  inflating: /tmp/.divx/include/common/FormatInfo.h  
   creating: /tmp/.divx/include/encoder/
  inflating: /tmp/.divx/include/encoder/Settings.h  
  inflating: /tmp/.divx/include/encoder/EncoderCallback.h  
  inflating: /tmp/.divx/include/encoder/FrameResult.h  
  inflating: /tmp/.divx/include/encoder/FrameOutput.h  
  inflating: /tmp/.divx/include/encoder/EncoderInterface.h  
  inflating: /tmp/.divx/include/encoder/FrameInput.h  
  inflating: /tmp/.divx/include/encoder/FeedbackInterface.h  
  inflating: /tmp/.divx/include/encoder/Cli.h  
  inflating: /tmp/.divx/include/encoder/DivXException.h  
   creating: /tmp/.divx/include/decoder/
  inflating: /tmp/.divx/include/decoder/LibQDec.h  
   creating: /tmp/.divx/lib/
  inflating: /tmp/.divx/lib/libdivx.so  
**cp: cannot stat `/tmp/.divx/include/*.h': No such file or directory**


I recieved that error too, but solved it by going to /home/***insertusrnamehere***/divx611-20060201-gcc4.0.1

and typing sudo ./install.sh

Or basically, the folder it puts right before all the files. An example:

"divx611-20060201-gcc4.0.1/docs/html/dir_000001.html" was shown, you would go to /home/usrname/divx611-20060201-gcc4.0.1" and type sudo "./install.sh"

Hope this helps!

---

### Post by saxuntu on 2007-10-06
> **lenninct said:**
> Just a quick note, make sure that you set your account to root instead of admin  underSystem/Administration/Users and Groups

Just select yoour account and hit properties, then under the Advanced tab, change the Main Group to Root instaed of Admin.

Hope this helps some ppl out there

Uhhh isn't this bad, setting your account to root? I thought one of the security features of Ubuntu was regular users didn't run in root unlike windows. Thats why theres sudo. Everything I've read says not make your account root.

---

### Post by bout10bucks on 2007-10-15
[http://ubuntu-unleashed.blogspot.com/2007/08/howto-get-divx-working-through-swiftfox.html](http://ubuntu-unleashed.blogspot.com/2007/08/howto-get-divx-working-through-swiftfox.html)

A little step through that will help you launch media files in an external player (VLC)

Helped me

---

### Post by fiskking on 2008-01-24
followed the steps (vlc is used to steam media in firefox , by the way) and tried to extract files to /usr/lib/vlc/codecs but did not have the right permissions.  Is this needed to play divx in vlc, streaming?

---

### Post by pressed on 2008-05-18
> **lenninct said:**
> Just a quick note, make sure that you set your account to root instead of admin  underSystem/Administration/Users and Groups

Just select yoour account and hit properties, then under the Advanced tab, change the Main Group to Root instaed of Admin.

Hope this helps some ppl out there

in my understanding, this is advice that no one should follow!
use sudo [command] when you want to perform commands as root. do NOT use a root account for everyday use.

---

### Post by h4mx0r on 2008-05-31
Use sudo su to get a root prompt. Far less key strokes that way than typing sudo every second or screwing your system in order to get some broken access to root.

---

