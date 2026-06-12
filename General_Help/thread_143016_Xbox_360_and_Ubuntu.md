---
title: "Xbox 360 and Ubuntu"
date: 2006-03-11
forum: General Help
---

### Post by Doytch on 2006-03-11
Does anyone know of an easy way to share their music/photos on an Ubuntu desktop with an Xbox 360?  I've seen some workarounds, like sharing a folder with another Windows computer through Samba and sharing that folder with the Xbox, but that won't work for me...

Thanks.

---

### Post by jimmer on 2006-03-12
You can use XBOX Media Center to easily view photos and video. To read more:[http://www.xboxmediacenter.com/](http://www.xboxmediacenter.com/)This program works well with the original Xbox. Just enable samba. I here the Xbox 360 has similiar features built in without hacking the Xbox. I'll don't own the 360 but I thought it could be easily done.

---

### Post by jimmer on 2006-03-12
It looks like the Xbox 360 uses media connect on Windows PC's to connect to the Xbox. I haven't come across anything stating it supports Linux. Since I don't have the 360 I have no way to test on Ubuntu. Good Luck.

---

### Post by knaveman on 2006-03-28
Try TwonkyVision. It worked for me with almost no fiddling around.

---

### Post by ArizonaKid on 2006-03-28
Why not just wait for the year 2010 to come around...18 versions of Windows Vista may be out...at leat one of them should work well with the XBOX 360.

---

### Post by talkingwires on 2006-05-02
[QUOTE=knaveman]Try TwonkyVision. It worked for me with almost no fiddling around.[/QUOTE]
I reluctantly agree with this post. I've been messing around with [uShare]("http://ushare.geexbox.org/") and [x360mediaserve]("http://sourceforge.net/projects/x360mediaserve/") for a month now, and neither of them work. There's no real information out there on getting Linux and the Xbox 360 talking to each other. Believe me, I've spent hours on Google and Yahoo looking. But the demo version of [TwonkyMedia]("http://www.twonkyvision.de/UPnP/index.html") worked great, or at least it worked great for the thirty minutes before the demo self-destructed. Since there isn't a free alternative, I'd wager that's your only bet.

---

### Post by zoward on 2006-08-12
I'm listening to music right now piped into my 360 from a Ubuntu share.  I'm using x360mediaserve ([http://sourceforge.net/projects/x360mediaserve/)](http://sourceforge.net/projects/x360mediaserve/)).  I'm running Dapper Drake 6.06 on an intel-based PC. I downloaded it to ~/tmp and extracted it from a zip file.  It's a java-based solution so you'll need java support.  From the README:


install lame,faad,flac and sox where they will be found by a bash script
run ./start

----------

To configure point your browser to [http://127.0.0.1:7000/configure](http://127.0.0.1:7000/configure) I suggest to test it you only point it at a small number such as a single album.


I configued it with my music directory (/home/me/music) and a friendly name (my PC's hostname).

Then I ran it with ./start from a command line window. No need to run with sudo as it uses a higher order port number (49152).

Went back to the 360 dashboard, Media page, Music, Computer and up came my music list.

Hope this helps,
zoward

---

### Post by zoward on 2006-08-12
A couple of extra notes to add:

- Once you launch the service, the job reads your entire msuic directory.  If you have a large directory, this could take a while.  I've been testing this on subsets of my full collection since it's pretty big (~30 GB), so fire this up on your full music directory at your own risk.

- It looks like you can bypass the web page entriely by adding (something like) the following to the file config.xml in the x360mediaswerve directory:

<Configuration>
        <FriendlyName>myhostname:1</FriendlyName>
        <MusicDir>/my/music/directory</MusicDir>
        <PCMOutput>0</PCMOutput>
</Configuration>

 - I haven't tested this with images yet.  To my knowledge, there is no video sharing with the 360.

---

### Post by Quicky on 2006-08-21
Hi Zoward, is there any chance you can help me out with this? I'm trying to get X360mediaserve to work, but after runnin bash ./start, after going through all my songs, produces this output at the end, and cannot be seen by the 360.

I don't really understand the error - can you give me any advice to correct?

```
21-Aug-2006 21:52:55 org.mortbay.util.Container start
INFO: Started org.mortbay.jetty.servlet.ServletHandler@1632c2d
21-Aug-2006 21:52:55 org.mortbay.util.Container start
INFO: Started HttpContext[/,/]
21-Aug-2006 21:52:55 org.mortbay.util.ThreadedServer start
WARNING: Failed to start: SocketListener0@fe80:0:0:0:20c:f1ff:fe11:2fbd%3:7000
21-Aug-2006 21:52:55 org.mortbay.http.SocketListener start
INFO: Started SocketListener on 127.0.0.1:7000
org.mortbay.util.MultiException[java.net.BindException: Cannot assign requested address]
```

Thanks

---

### Post by cpete on 2006-08-24
> **Quicky said:**
> Hi Zoward, is there any chance you can help me out with this? I'm trying to get X360mediaserve to work, but after runnin bash ./start, after going through all my songs, produces this output at the end, and cannot be seen by the 360.

I don't really understand the error - can you give me any advice to correct?

```
21-Aug-2006 21:52:55 org.mortbay.util.Container start
INFO: Started org.mortbay.jetty.servlet.ServletHandler@1632c2d
21-Aug-2006 21:52:55 org.mortbay.util.Container start
INFO: Started HttpContext[/,/]
21-Aug-2006 21:52:55 org.mortbay.util.ThreadedServer start
WARNING: Failed to start: SocketListener0@fe80:0:0:0:20c:f1ff:fe11:2fbd%3:7000
21-Aug-2006 21:52:55 org.mortbay.http.SocketListener start
INFO: Started SocketListener on 127.0.0.1:7000
org.mortbay.util.MultiException[java.net.BindException: Cannot assign requested address]
```

Thanks

I had a similiar issue after installing sun jvm. Although it doesn't make sense as why change of virtual machine would cause this error. Anyways heres how I fixed my problem.

From the README
```
If you get errors about could not open socket try adding the ip after the start
script e.g ./start 192.168.0.1
```

Hope it helps, and remember RTFM :twisted:

---

### Post by Quicky on 2006-08-28
Did you have a similar issue, or the same issue? That solution didn't work for me, manual or no manual.

---

### Post by Perkabalo on 2007-03-07
Has anyone been able to play flac files? Mp3's working fine, but flac wont start.

First i got some error message that prompted no acess to the flacpcm file in ScriptDir, changed permission and now i get this message:

```
java.io.IOException: Cannot run program "/home/perkabalo/Desktop/xmediaserve/ScriptDir/flacpcm" (in directory "/home/perkabalo/Desktop/xmediaserve/ScriptDir"): java.io.IOException: error=2, No such file or directory
```

Any thoughts? \\:D/

---

### Post by cszikszoy on 2008-03-11
This is a great program (x360MediaServe)

Would be even more amazing if someone could make a gtk gui for it though.  With all of the configuration data stored in the xml file, I don't imagine that it would be too complicated?

:)

Thanks for the tip!

---

