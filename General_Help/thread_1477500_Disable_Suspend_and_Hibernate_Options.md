---
title: "Disable Suspend and Hibernate Options"
date: 2010-05-08
forum: General Help
---

### Post by Tlosk on 2010-05-08
I was looking for a way to disable the Suspend and Hibernate options from the logout menu as my laptop hangs on both and requires unplugging/battery removal to restart.

I found a few pages with instructions for older Ubuntu versions but I didn't come across anything that applied directly to 10.04 Lucid Lynx so I thought I'd post what I found worked for me on 10.04.


[LIST=1]
[*]Open a Terminal from the Applications>Accessories>Terminal.
[*]Because the file you will be editing requires root privileges to edit, you will need to use the sudo command:```
sudo gedit  /usr/share/polkit-1/actions/org.freedesktop.upower.policy
```
[*]Enter your password. This will then open the settings file in the text editor with the needed permissions (opening the file directly with the editor you will get an error message if you try to save the file).
[*]There are two sections in this file, the first for suspend and the second for hibernate. Near the end of each section will be a line with:```
<allow_active>yes</allow_active>
```
[*]Change this from Yes to No to disable. Save the changes and reboot.```
<allow_active>no</allow_active>
```
[*]Now the power menu will not display these options. To reverse changes just repeat the above and change from no back to yes.
[/LIST]

---

### Post by The Real Dave on 2010-05-08
Thank you. This had been a minor annoyance for me, because Suspend and Hibernate don't work for me either, and I often accident trigger them. 

I hope you don't mind, but I made a blog post of this, which can be found [here]("http://wp.me/pIF7C-6U").

Also, it's preferable to use gksudo instead of sudo when opening graphical programs, to prevent permission errors :)

---

### Post by GabeSmall on 2010-06-14
Thank you!!!

I have a Lucid Wubi installation on an AMD Turion Mobile M640 that I bought pre-installed with Windows 7 Pro just a little over a week ago.  When I made the mistake of Hibernating Ubuntu I was convinced that I'd blown up my new computer when nothing I did brought it back from a blank screen. Fortunately I was able to regain the presence of mind to power down, disconnect the power, remove the battery, and in the meantime go look for a solution using my wife's laptop.

The battery removal had done the trick to allow me to get back to the boot loader, but if I tried to boot Ubuntu, I got a sort of a frozen splash screen and that was it. I discovered a solution for waking Ubuntu up from the boot menu here: [http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html](http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html)

Not wanting to put myself through that again, though, I sought a way to disable the option altogether, but nothing I found seemed to apply (for instance, disabling instructions for earlier releases had me searching for the "can_hibernate" key in the Configuration Editor--don't bother looking for it in Lucid; it's not there) until I found your simple solution.

BTW, the solution you describe disables the Suspend and Hibernate options from the Ctrl+Alt+Del menu, as well. Sweet!

---

### Post by karthick87 on 2010-06-14
I have been searching this information,thanks a lot :)

---

### Post by Open4D on 2010-07-18
> **GabeSmall said:**
> BTW, the solution you describe disables the Suspend and Hibernate options from the Ctrl+Alt+Del menu, as well. Sweet!

Confirmed.  And that aspect even seemed to take effect before rebooting.


Anyway, thank you Tlosk!  This is just what I wanted.

Some experts and/or people with lots of time or slightly different requirements might also wish to look at [this page]("http://my.opera.com/linuxonlinehelp/blog/ubuntu-10-04-lucid-lynx-disable-hide-reboot-shutdown-standby-suspend-gnome-syste"), which I came across on my way to finding Tlosk's solution.

---

### Post by sinha1612 on 2010-07-25
Have been looking for this since I have a Wubi install and don't want those options for the damage they might do... So thanks a bunch! :)

---

### Post by DavidBiesack on 2011-09-28
Interesting. I made these changes (10.10) and it has no effect. The power tool on my desktop still has active Suspend and Hibernate menu items, and Ctrl-Alt-Del still has Suspend and Hibernate. 

This shows the result of edit I made via sudo:

```
# grep allow_active  /usr/share/polkit-1/actions/org.freedesktop.upower.policy
      <allow_active>no</allow_active>
      <allow_active>no</allow_active>
```

There are lots of obsolete instructions pages on how to disable these via gconf-editor etc. and none work. I need to disable these because when my system goes into suspend, it won't wake up and I must power off/on, which is **not** good.

---

### Post by dcottingham on 2012-07-25
If you wound up here looking to the answer, as I did: It appears that the format of the polkit files has changed since this thread was written, and this will no longer work. To get a solution that works now, see this link:
[http://askubuntu.com/questions/93542/how-to-disable-shutdown-reboot-suspend-hibernate](http://askubuntu.com/questions/93542/how-to-disable-shutdown-reboot-suspend-hibernate)
But I did have to get creative with the file names -- I just successfully did this on an 11.04 system, and I put the file in "/etc/polkit-1/localauthority/50-local.d". The file name must end in .pkla, otherwise arbitrary (I think the one thing is there must be no other pkla file on the system with the same name). After setting up the file, you might need a logout-login, and the offending menu entries are gone.

---

