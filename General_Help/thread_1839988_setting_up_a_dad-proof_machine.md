---
title: "setting up a dad-proof machine"
date: 2011-09-06
forum: General Help
---

### Post by awambawamb on 2011-09-06
hi people!

I've always installed Ubuntu all alone, without problem... but in those days I've came to face a more complex problem.

My dad would like to have his computer, "to write things, surf the web, check the mail". Nothing more nothing less.
I'm going to lend him my 6yo laptop, an HP zd8369ea that will use the 32" tv screen (full HD) as monitor. He asked about a computer that will be simple and protected by virus and malware etc., so why don't give a try to Ubuntu...

What I'm planning to do it to create a computer with two accounts, mine as Admin and my dad's as a User. I'd like to set up his account so that he won't be able to change the system, nor he could be tempted to. I'd like to hide systems menu as well. To help him, I'm planning a desktop with four big icons

Firefox
Thunderbird (set up to his mail account)
OpenOffice
Shutdown **<-- Question: how i can create an icon for the shutdown?**

XFCE could help me creating a clean desktop?

Another big problem I'm facing is that he would like me to control the pc remotely though the web, as I'll be far away in those times and he thinks that he would need help... is that possible? I had experience of helping my friends with LogMeIn, but nothing more!

Thanks for reading!
Max

---

### Post by ajgreeny on 2011-09-06
For shutdown icon see [http://ubuntuforums.org/showthread.php?t=342763](http://ubuntuforums.org/showthread.php?t=342763)
and [http://ubuntuforums.org/showthread.php?t=1078884](http://ubuntuforums.org/showthread.php?t=1078884)

---

### Post by 23dornot23d on 2011-09-06
If you use Gnome Shell ..... you can set it with minimal but useful icons .....

Also with Cairo-Dock ..... you can drag and drop the Shutdown Icon onto the screen .....

[_***SCREENSHOT***_]("http://img683.imageshack.us/img683/3792/shutdown2.jpg")

You can place the shutdown Icon where you want to .. ....

everything dims down as you are about to exit .....

[IMG]http://img64.imageshack.us/img64/3792/shutdown2.jpg[/IMG]

---

### Post by JKyleOKC on 2011-09-06
Most of what you're looking for will be achieved simply by installing Ubuntu or Xubuntu on the machine. When you do a clean install, the user that you create during the install process is made a member of the "admin" group and thus is able to use "sudo" to make system changes. Users that you create later do not get this capability automagically although you can add it at any time. If you set a strong password on that first user during the install process, then immediately after installing create a new user for your dad, you'll be most of the way there! His ID will not be able to make any critical system changes, but yours will be via "sudo."

To simplify it for him, you can set the system to log his user in automatically at power-on time, so he doesn't have to make a choice. When you need to do system work, you can switch to a different virtual terminal via CTRL-ALT-F2 and log in with your ID, if you're at the machine. You can also set up SSH capability including automatic login to your ID, for the remote access need, but I don't know the exact details of doing this so you'll have to do some searching.

For his limited desires, I recommend Xubuntu rather than Ubuntu, since it has far fewer bells and whistles that might get him in trouble. The underlying system is the same in both; the difference is mostly in the window manager itself and the accessories installed by default.

---

### Post by pqwoerituytrueiwoq on 2011-09-06
for the shut down icon i saw this in a thread earlier
make a launcher to run this command
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```
script that will ask to confirm
```
#!/bin/sh
if [ $(zenity --question --title="Are you sure?" --text "Are you sure you want to turn the computer off?"; echo $?) = "0" ]; then
dbus-send --system --print-reply --dest=org.freedesktop.Hal  /org/freedesktop/Hal/devices/computer  org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
fi
```

---

### Post by linuxuser12345 on 2011-09-06
Using the default Unity configuration sounds like a good way, if you ask me. It has big, simple, easy to find icons, an excellent search tool, and a simple overall appearance. Go with Unity.
You will probably want to use the Unity 2D version available in the Software Center, as your system is older.

---

### Post by grahammechanical on 2011-09-06
You should start by giving your father some credit for having a brain.

And do not forget to set up a bookmark to this forum. Will you need to work out a username and password for him? Let him work out how to register himself. He needs to keep his brain active or he will become senile.

I am 63, by the way, and I have not yet given up learning new things.

Regards.

---

### Post by awambawamb on 2011-09-07
Thanks everyone, I'll try this in some days after my exams. Still searching for some remote control though, it would be helpful!

Between the 2 windows manager I think I'll choose XFCE, Unity "fried" my laptop's monitor due excessive heat :(

*[SIZE="1"]I'm sorry if it seemed that I'm not giving respect to my dad, but he's going 70 and doesn't speak a single word of english, just italian and a bit of french. He hates computers also, but he needs them to work... the italian Stakanovich! at least, I'm giving him some knowledge of open source ;)[/SIZE]*

---

### Post by JKyleOKC on 2011-09-07
For remote control, investigate SSH. Set up properly and left running in background, it will give you access for maintenance purposes although it's only a command-line interface. You might look also at VNC and "Remote Desktop" for using a GUI to walk him through problems, but both of them offer much higher security risks. No machine connected to the Internet can ever be totally secure, of course, but the remote GUI programs are among the favorite targets of the script kiddies...

---

### Post by Myglaren on 2011-09-10
> **grahammechanical said:**
> You should start by giving your father some credit for having a brain.

And do not forget to set up a bookmark to this forum. Will you need to work out a username and password for him? Let him work out how to register himself. He needs to keep his brain active or he will become senile.

I am 63, by the way, and I have not yet given up learning new things.

Regards.

Good advice.  I am also 63 and have very few problems but have been pottering around with computers for quite a while but to illustrate the validity of the quoted post, my wife is, or was until recently, completely unfamiliar with computers.

I bought her an older laptop and installed 10.04 on it with no special mods.  After a few days helping her with it she very rarely has any difficulty. Usually it is the grandchildren rearranging her desktop that throws her a bit.*
She uses it primarily for web browsing, emailing her friends and the rest of the family, downloading and sharing her photo's (she recently bought a digital camera as her phone wasn't quite up to her requirements)she also runs her music CDs, DVDs, shares music etc.  

*She is also legally blind so has that problem to overcome too.  She will be 60 in a few days.

---

