---
title: "Terminal window will not stay open"
date: 2010-06-12
forum: General Help
---

### Post by Himaji on 2010-06-12
I'm practically just installed linux on my macbook air. I finally got the sound to work, shut down my computer and when it loads back up, terminal won't open. Well, it will but only for a split second then the window disappears.
I would try:
[https://www.centos.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=20540&forum=38](https://www.centos.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=20540&forum=38)
But I can't find the file it describes.
I would also try:
[http://ubuntuforums.org/showthread.php?t=749850&highlight=gnome+terminal+won%27t+stay+open](http://ubuntuforums.org/showthread.php?t=749850&highlight=gnome+terminal+won%27t+stay+open)
But my functions keys won't work yet and I don't know how to start a new launcher.

I'm still very new at this, help?

---

### Post by gingivere0 on 2010-06-12
Bump, I don't have an answer, but I'm interested in finding out why/how.

---

### Post by pastalavista on 2010-06-12
If you hold down the "shift" key at the first splash screen, it will open the grub boot loader and you can select to boot in "recovery mode" and can access a terminal console there. You can also run broken package and filesystem checks automatically.

---

### Post by prodigy_ on 2010-06-12
Does Ctrl+Alt+F1 work?

---

### Post by Himaji on 2010-06-13
First, Ctrl+Alt+F1 does not work-function keys don't work
second, I loaded up recovery mode - ran both broken package and system check but how do I access terminal there?

---

### Post by MooPi on 2010-06-13
Try Alt + F2 , which should give you a run dialog. From this you should be able to run a terminal, try ```
xterm
``` This should give you a terminal until you can fix the gnome-terminal issue. Your gnome-terminal profile is stored on an .xml file in /home/user/.gconf/apps/gnome-terminal/profiles/Default. Can you post the contents ?

---

### Post by pastalavista on 2010-06-13
> **Himaji said:**
> First, Ctrl+Alt+F1 does not work-function keys don't work
second, I loaded up recovery mode - ran both broken package and system check but how do I access terminal there?In recovery mode, the option for a root console (terminal) is in the list of choices. One is a root terminal with networking and one without networking. The networking won't work if you use proprietary wireless drivers but ethernet cable or kernel-module wireless drivers will probably work.

---

### Post by Himaji on 2010-06-13
> **MooPi said:**
> Try Alt + F2 , which should give you a run dialog. From this you should be able to run a terminal, try ```
xterm
``` This should give you a terminal until you can fix the gnome-terminal issue. Your gnome-terminal profile is stored on an .xml file in /home/user/.gconf/apps/gnome-terminal/profiles/Default. Can you post the contents ?
okay function keys don't work, I tried it anyway, but it didn't work. however, pastalavista explained that i could use terminal in recovery mode. i ran xterm in the root console without networking (i can do it in networking if necessary)
here is what it read:
Warning: This program is an suid-root program or is being run by the root user. The full text of the error or warning message cannot be safely formatted in this environment. You may get a more descriptive message by running the program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %S
xterm: DISPLAY is not set

/home/user/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml :

<gconf>
&#8722;
<entry name="visible_name" mtime="1276476683" type="string">
<stringvalue>Default</stringvalue>
</entry>
<entry name="alternate_screen_scroll" mtime="1276476683" type="bool" value="true"/>
&#8722;
<entry name="palette" mtime="1276476683" type="string">
&#8722;
<stringvalue>
#2E2E34343636:#CCCC00000000:#4E4E9A9A0606:#C4C4A0A00000:#34346565A4A4:#757550507B7B:#060698209A9A:#D3D3D7D7CFCF:#555557575353:#EFEF29292929:#8A8AE2E23434:#FCFCE9E94F4F:#72729F9FCFCF:#ADAD7F7FA8A8:#3434E2E2E2E2:#EEEEEEEEECEC
</stringvalue>
</entry>
&#8722;
<entry name="background_color" mtime="1276476683" type="string">
<stringvalue>#FFFFFFFFDDDD</stringvalue>
</entry>
&#8722;
<entry name="foreground_color" mtime="1276476683" type="string">
<stringvalue>#000000000000</stringvalue>
</entry>
&#8722;
<entry name="bold_color" mtime="1276476683" type="string">
<stringvalue>#000000000000</stringvalue>
</entry>
</gconf>

---

### Post by pastalavista on 2010-06-13
You don't need xterm because you're already in the root console. You need to run the commands you found in the console itself. You only need networking if you have to download packages. Have you tried rebooting since the recovery mode package and fsck?

OK never mind all that, boot all the way and login to your setup. Open your home directory with nautilus, show hidden files (ctrl+h) and look for a folder named .gconf (a dot before the name is how you know it's hidden).. in the .gconf folder open apps/gnome-terminal/profiles and delete the file %gconf.xml and the default folder then log out and back in.

---

### Post by Himaji on 2010-06-15
Yes, I have been rebooting after everything I've tried so far. (though I may be shutting down from recovery mode incorrectly-is there any special way?)

Alright, I found the file-moved it to the trash-emptied trash. Rebooted, terminal still doesn't work I tried it one more time to make sure I did it right.

---

### Post by pastalavista on 2010-06-15
Well, I'm stumped. You say you just installed, so is everything else, wireless, audio, etc working ok? Have you run all the updates?

---

### Post by pastalavista on 2010-06-15
Also, in the System/Preferences/Keyboard app, under the layout tab, there are many different Apple models to choose from. You might find one which lets the F-keys work.

ps. You might also try installing different terminals. I like 'tilda' (opens with the ` key) but there are several other "terminal emulators" available in the repos.

---

