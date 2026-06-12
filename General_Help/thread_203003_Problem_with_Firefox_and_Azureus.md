---
title: "Problem with Firefox and Azureus"
date: 2006-06-24
forum: General Help
---

### Post by sdyson on 2006-06-24
When I click a torrent link in Firefox the file is handled automatically by Azureus by I got a message along the lines of: 

Failed to access torrent file 'file:///tmp/{snip}.torrent Ensure sufficient temporary file space is available (check browser cache usage)

I checked to make sure the torrent file referenced actually existed in the /tmp directory and it did but I discovered that the permissions on it were set so that only the owner (me) could read it. I assume that Azureus is trying to read it as another user and hence it fails. 

Has anyone else had this problem and found a workaround? I'm now having to copy torrent links and paste them into Azureus which isn't a great solution.

---

### Post by rai4shu2 on 2006-06-24
I don't have Azureus, but it may be something in Azureus. Here's a discussion of the problem in Gentoo:

[http://suksit.blogspot.com/2006/04/fixing-azureus-error-messages.html](http://suksit.blogspot.com/2006/04/fixing-azureus-error-messages.html)

---

### Post by sdyson on 2006-06-26
Thanks, but it looks like that is a different bug. Azureus is trying to open an empty string. In my case the a valid filename is passed to Azureus but it has the  wrong file permissions.

---

### Post by ohgod on 2006-06-26
I used to get this error with Azureus all the time.  I think it was a problem with the java runtime not giving Azureus enough virtual memory, but that's just a guess (I never did figure it out).  I doubt it's a permissions issue, as Azureus should be running as the same user as Firefox.

Might want to try out another bittorrent client (the official one is pretty nice, though it doesn't have as many features of Azureus).

---

### Post by mlind on 2006-06-26
How have you setup firefox that it opens .torrent files with Azureus?
I couldnt get it working by using ~/.mailcap, so I did a small script

```

#!/bin/sh

AZ_PATH=/path/to/azureus
exec $AZ_PATH/azureus "$@"

```

which I use to "open" .torrent file on browsers.

---

### Post by sdyson on 2006-06-26
Nothing as complicated as that. The first time I click a torrent URL I was offered a dialog to choose the program to open it. I selected Azureus and then checked the "perform this action every time" box.

---

### Post by mlind on 2006-06-26
[QUOTE=sdyson]Nothing as complicated as that. The first time I click a torrent URL I was offered a dialog to choose the program to open it. I selected Azureus and then checked the "perform this action every time" box.[/QUOTE]

okay. I have Azureus installed locally so I found this as my best option.

Look for "azureus" script on Azureus' folder, and make sure the last line looks like

```

${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main **"$@"**

```

The bolded part is important and need to be in quotation marks, or otherwise
.torrents with whitespaces on their names don't open up correctly.

I'm not sure if it's related to your problem though.

---

### Post by Tristan9669 on 2006-07-02
[QUOTE=mlind]okay. I have Azureus installed locally so I found this as my best option.

Look for "azureus" script on Azureus' folder, and make sure the last line looks like

```

${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main **"$@"**

```

The bolded part is important and need to be in quotation marks, or otherwise
.torrents with whitespaces on their names don't open up correctly.

I'm not sure if it's related to your problem though.[/QUOTE]
I can't find the azureus script you're talking about...

---

### Post by sdyson on 2006-07-07
> **mlind said:**
> 
```

${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main **"$@"**

```

The bolded part is important and need to be in quotation marks, or otherwise
.torrents with whitespaces on their names don't open up correctly.


Yep, I have the same part in quotes so that isn't the problem. I'm finding that some torrents work, others don't but there's no obvious difference between them. Strange.

---

### Post by jimmygoon on 2006-07-07
Mine does this all the time as well, of course Azureus also has problems with the toaster popups >_<

Anyways, it has never worked for me... It throws that error for me and I just give up and save it to my desktop...

---

### Post by mlind on 2006-07-07
This could be more firefox problem than Azureus. I'm using my custom launcher and I haven't had the problem you described. Only problem with long filenames, which was error on my part.

---

### Post by sdyson on 2006-07-13
Been playing with this a bit more. 

I'm still having the problem opening some torrents from firefox and discovered that it also fails if I try pasting the URL directly into Azureus so that means Firefox is not the problem. If I save the torrent file to hard disk and open it from there then it works. 



I fixed the toaster problem that jimmygoon mentioned by installing the latest version from the azureus website. This also fixes the problem with the icon not showing up in the system tray area.

---

### Post by Epperly on 2006-07-20
I'm having this problem, too... When I save the .torrent to disk though, it still doesn't work.

---

### Post by Epperly on 2006-07-20
sdyson: I fixed the problem(so far), by doing a sudo apt-get remove firefox (to uninstall it), then install it again with sudo apt-get install firefox.

So far, the torrents have started working again, hopefully they won't crap out anytime soon, though(meaning I hope reinstalling isn't a temporary fix)

[edit]nevermind, it's already doin it again :([/edit]

---

### Post by gkiller on 2006-10-10
Any news or solutions to this problem yet?

I have the same problem. I always download the torrents to my HDD and the open them from there. If I open the files through Nautilus (double-clicking on them), then I get this "Not a file, check temp space" error. But if I drag&drop the torrent into the Azureus window, or if I open the downloaded torrent directly from Azureus via the menu, then it works as it should.

The funny thing is, it worked until a few days ago. I didn't do anything special, but I of course installed security and other updates through update-manager, and I also have dapper-backports repository activated. But I don't know if the problem has anything to do with any recent updates.

I am using Azureus 2.5.0.0 which I downloaded and installed over the older version from Synaptic.

---

### Post by matt_risi on 2006-10-11
Azureus has always ALWAYS given me trouble too, and I wish so much it would work properly because it's the only resonably good torrent program available for Ubuntu. BiTornado BLOWS, same with the default package. Every time I try to use Azureus, I get error messages, followed by Azureus crashing and then the ERROR MESSAGE CRASHING, being stuck on my desktop, making me restart x. Pain in the butt.

---

### Post by annonymoususer on 2006-10-22
I had a similar error message.

Try setting your Files -> Performance Options -> Size of Cache in MB, setting to default if you changed it, default is around 10, if it's any higher then that, it might be the source of your problems.

---

### Post by chefounet on 2006-10-29
Hi everyone, I'm new in the world of Ubuntu and I have the problem of opening torrents with Azureus too.
What I don't understand is that the problem didn't occur the first time.
I manage it by saving the .torrent files for the moment, but it's not at all practical... why has he been kind the first time ? Dunno...
Besides, Azureus doesn't want me to increase the size of my cache, for the moment I have 1Mb...
Sure the client works better on windows for the moment !

---

### Post by bignickel on 2006-11-02
I think I might have fixed it.  I'm running azureus 2.5.0.0 and so far it's worked for me.

```
sudo nano /usr/bin/azureus
```

Change
```
/opt/azureus/azureus $*
```

To
```
/opt/azureus/azureus "$*"
```

Let me know if that works.

---

### Post by sdyson on 2006-11-02
Azureus from the ubuntu repositories is still on 2.4. It doesn't have the line of code you just posted although the equivalent line is already quoted.

---

### Post by bignickel on 2006-11-02
Yeah I installed 2.5.0.0 using [this howto]("http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus") because 2.4 (out of the repos) would crash everytime it opened (which is now reported as a bug as far as I know).  So with 2.5.0.0 it would start, but then have problems opening torrents.  This fix worked for me.

---

