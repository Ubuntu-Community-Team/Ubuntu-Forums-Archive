---
title: "Booting into Terminal"
date: 2010-10-02
forum: General Help
---

### Post by ki4jgt on 2010-10-02
I want to force the user to login from the Terminal before the can see the desktop. Please and Thank You

---

### Post by dcstar on 2010-10-02
> **ki4jgt said:**
> I want to force the user to login from the Terminal before the can see the desktop. Please and Thank You

What do the hundreds of posts already on booting to a terminal say?

---

### Post by soryu on 2010-10-02
Tell me.
I Command  IT.














HeynoW.

---

### Post by Noz3001 on 2010-10-02
Would disabling GDM do the trick?

---

### Post by ki4jgt on 2010-10-02
Have no clue, I can't find any of these supposedly hundreds of forums. Google is too broad in it's search terminology and the Ubuntu search box is too. How would you go about disabling GDM?

---

### Post by spupy on 2010-10-02
> **ki4jgt said:**
> Have no clue, I can't find any of these supposedly hundreds of forums. Google is too broad in it's search terminology and the Ubuntu search box is too. How would you go about disabling GDM?

Remove GDM/KDM from startup services. (or whatever it is called in ubuntu).
System -> Administration -> Services (I'm not on ubuntu so I can't  check it.)
(or so says the 3rd google result for "ubuntu disable gdm boot"... ahem)

Ubuntu will boot to tty1. Log in there. Type startx. Probably nothing will happen, or some ugly window manager will open. If you don't get gnome, you will need to enter some stuff in the file "~/.xinitrc":
```
exec gnome-session
```

---

### Post by oldos2er on 2010-10-02
If you're using grub2, edit /etc/default/grub, change GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to GRUB_CMDLINE_LINUX_DEFAULT="text"

Edit: Now run ```
sudo update-grub
``` to finalize the changes you made.

After login enter startx to start the GUI.

---

### Post by btindie on 2010-10-02
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1570089").
 
I've also heard of problems with sound when started this way.

---

### Post by jtwdyp on 2010-10-09
> **oldos2er said:**
> If you're using grub2, edit /etc/default/grub, change GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to GRUB_CMDLINE_LINUX_DEFAULT="text"

After login enter startx to start the GUI.

Pardon me for jumping in to this thread. But I've always booted to console and used startx when I wanted a gui...  But I'm not used to grub2 at all.

With *buntu I've always used update-rc.d to accomplish the console boot. Though recently neither gdm nor kdm seem to respect the rc.d settings. And simply uninstalling the display manager led me to some annoying pop-up error menus at boot. So I installed a simpler display manager (slim) which still listens to the rc.d settings. ```
sudo update-rc.d -f slim remove
sudo update-rc.d slim stop 20 2 3 4 5 .
``` But if I can use some kind of kernel option to do this regardless of which display manager is installed then that's even better.

But like I said I'm lost with grub2. You mention editing /etc/default/grub to effect such a change.
I opened that file on an old laptop that I'm experimenting with and in addition to the line you say to change I see two others that I'm curious about:```
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
``` Which sounds more like what I'd need to do to accomplish this without installing slim and running the above update-rc.d commands. But what does it mean by "grub-pc only"???

the second is perhaps a bit off topic but I'd want to do this at the same time...

```
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
``` Which would interest me greatly if I knew how to tell it to use human readable LABEL such as what in a classic grub menu.lst would look like:```
kernel  /boot/vmlinuz-2.6.32-24-generic root=LABEL=UbuntuLucidRoot ro vga=normal
``` instead of the UUID method.(Of course I'd have to have used e2label to set the label first...)

Oh and as long as I'm asking about editing /etc/default/grub, I might as well ask how to tell it I want it to put up a "text" grub menu that includes the existing in /boot/grub/grub.cfg:```
menuentry "Memory test (memtest86+)"
``` entry for longer than a nanosecond before it automatically boots ubuntu???
And lastly hows does one get it to rebuild the /boot/grub/grub.cfg with the changes in /etc/default/grub???

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

### Post by oldos2er on 2010-10-09
> **jtwdyp said:**
> 
And lastly hows does one get it to rebuild the /boot/grub/grub.cfg with the changes in /etc/default/grub???

Run ```
sudo update-grub
``` after you've made your changes.

As to your other questions, They've mostly been answered by people far more experienced and knowledgeable than I:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

Hope that helps.

---

### Post by sisco311 on 2010-10-09
> **jtwdyp said:**
> 

With *buntu I've always used update-rc.d to accomplish the console boot. Though recently neither gdm nor kdm seem to respect the rc.d settings. 

Ubuntu uses upstart: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

gdm, kdm & lxdm are using upstart jobs, while slim still uses a System-V style init scrip. 

The **text** kernel parameter only disables the display managers which are using upstart jobs. 

The name of default display manager is stored in /etc/X11/default-display-manager. Both upstart jobs and System-V style init scripts are using this file to determine which display manager to start.  

So, in order to disable any display manager, one could simple edit the content of this file.

i.e.:
```
echo "none" | sudo tee /etc/X11/default-display-manager
```

and to re-enable a display manager, i.e. gdm:
```
echo "/usr/sbin/gdm" | sudo tee /etc/X11/default-display-manager
```

---

### Post by ki4jgt on 2010-10-09
Booting grub into text, how do you get the gnome-keyring to stop coming up after you startx

---

### Post by jtwdyp on 2010-10-10
On Sat Oct 9 Sisco311 said:> Ubuntu uses upstart: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

gdm, kdm & lxdm are using upstart jobs, while slim still uses a System-V style init scrip. 

The **text** kernel parameter only disables the display managers which are using upstart jobs. OK then assuming I use a display manager that uses upstart, I can now control this with the kernel parameter "**text**" in *buntu the same way I could use "**nox**" with sabayon or "**3**" with either OpenSuSE or PCLinuxOS... Kool! I like the ability to use dual grub menu entries to allow choosing at boot time if I want a display manager or not... This means I'll have to consider switching my desktop and/or my primary laptop back to gdm or kdm so that I can use "**text**" as a switch. Food for thought, this is.

Thank you for including the "why" in your explanation. I always understand better when I can get a good grasp on the why...

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

### Post by jtwdyp on 2010-10-10
On Sat Oct 9th oldos2er did say> Run ```
sudo update-grub
``` after you've made your changes.DUH Now I feel kinda dumb, That much I shoulda been able to get...

> As to your other questions, They've mostly been answered by people far more experienced and knowledgeable than I:
<<SNIP>>
> Hope that helps.Yup Those references were very useful in figuring this durned grub2 stuff out. **Except**, wouldn't you know, for the bit about using "LABEL=**HumanReadableLabel**" instead of using "UUID=**HorridGarbageString**"

But inspired by the nice links you left me, I tried a scroogle search for "**ubuntu grub2 LABEL=**" and waded through a lot of <expletive deleted> and **almost** figured it out. I used the /etc/grub.d/40_custom file as a template for a 06_custom file to put my manualy configured choice at the top of the grub2 menu. And cobbled together this:```
menuentry 'Ubuntu, Lucid 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	insmod ext2
	search --no-floppy --label UbuntuLucidRoot1 --set 
	linux	/boot/vmlinuz-2.6.32-21-generic root=LABEL=UbuntuLucidRoot1 ro gfxpayload=text
	initrd	/boot/initrd.img-2.6.32-21-generic
}
```Which almost works right. That is it works except that upon selecting it from grub, I get an error message that says the device "UbuntuLucidRoot1" doesn't exist. Then it goes ahead and boots it anyway...

As far as whether it exists I offer this bit of snipage:```
JtWdyP -> /home/jtwdyp
> ls -l /dev/disk/by-label
total 0
lrwxrwxrwx 1 root root 10 2010-10-10 01:44 MySwap-5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-10-10 01:44 UbuntuLucidRoot1 -> ../../sda1
JtWdyP -> /home/jtwdyp
> 

```If anyone can tell me what's wrong with the above menuentry that causes the device "UbuntuLucidRoot1" to be momentarily **NOT** recognised. And then used anyway???

thanks

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

### Post by sisco311 on 2010-10-10
> **jtwdyp said:**
> On Sat Oct 9 Sisco311 said:OK then assuming I use a display manager that uses upstart, I can now control this with the kernel parameter "**text**" in *buntu the same way I could use "**nox**" with sabayon or "**3**" with either OpenSuSE or PCLinuxOS... Kool! I like the ability to use dual grub menu entries to allow choosing at boot time if I want a display manager or not... This means I'll have to consider switching my desktop and/or my primary laptop back to gdm or kdm so that I can use "**text**" as a switch. Food for thought, this is.

Thank you for including the "why" in your explanation. I always understand better when I can get a good grasp on the why...

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

Yep, but if you prefer slim over gdm or kdm, you could *tweak* its init script to feet your needs.

/etc/init.d/slim:
```
...
 case $1 in
  start)
    [b]# Check kernel command-line for inhibitors
    for ARG in $(cat /proc/cmdline)
    do
      case "${ARG}" in
        text|-s|s|S|single)
          echo "Not starting X display manager (slim); booting into text mode =)" 
          exit 0
          ;;
      esac
    done[/b]

    if [ "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" ] &&
       [ -e $DEFAULT_DISPLAY_MANAGER_FILE ] &&
       [ "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
      echo "Not starting X display manager (slim); it is not the default display manager."
    else
      echo -n "Starting X display manager: slim"
      start-stop-daemon --start --quiet $SSD_START_ARGS || echo -n " already running"
      echo "."
    fi
  ;;
...
```

And if you are using Grub2 and want to create separate text & GUI menu entries check out [this]("http://ubuntuforums.org/showthread.php?p=9584414#post9584414").

---

### Post by jtwdyp on 2010-10-13
> **sisco311 said:**
> Yep, but if you prefer slim over gdm or kdm, you could *tweak* its init script to feet your needs.

/etc/init.d/slim:
```
...
<<< code deleted to conserve bandwidth >>>
...
```
> And if you are using Grub2 and want to create separate text & GUI menu entries check out [this]("http://ubuntuforums.org/showthread.php?p=9584414#post9584414").Thanks for that tweak, It may yet prove useful... Though as of yet the only reason I preferred slim was that prior to learning about the "text" kernel option, the only way I knew to get an installed display manager to permit booting to console in  *buntu was via the update-rc.d method that gdm no longer respected...

Actually (thanks to this thread) I've now been able to use the files: 
/etc/default/grub, /etc/grub.d/* (including "06_custom") to get 90% of what I was looking for. That is to say everything except getting the console to use the old toshiba satellite's entire screen for it's 80 column's of text. What it does in the text console is to put a border of nearly an inch of blank space around the usable text area...

Once I run startx, I get by default an 800x600 screen that fills the display. But consoles such as tty1 refuse to use the whole screen.
I ***can*** live with it. but I would like the text mode tty to use the whole screen. Could you suggest a way to do that with the 80 col consoles?? 
-- 
jtwdyp
J(tWdy}P
Joe(theWordy)Philbrook
-- 
jtwdyp
J(tWdy)P
Joe{theWordy)Philbrook

---

### Post by jtwdyp on 2010-10-22
> **ki4jgt said:**
> Booting grub into text, how do you get the gnome-keyring to stop coming up after you startx

Sorry it took so long to reply, but to tell you the truth I didn't notice the question till this morning. I'm afraid that I don't know much about the gnome keyring... I'm thinking that if it's "coming up" on your desktopm you must be talking about some graphic control panel???

I presume that there must be a setting in gnomes configs to control that behavior. I've rarely used gnome though, so I can't say just where it would be. I can say that I've used startx for years and never had any application etc... pop up by itself that I hadn't either used some desktop specific "save session" or "remember window" tool, or specificly called in my ~/.xinitrc. etc... Startx by itself isn't the reason. (does the keyring "come up" when you use gdm to start a session???)
-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

