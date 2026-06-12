---
title: "Screen Brightness Problems"
date: 2011-08-28
forum: General Help
---

### Post by c0dez0r on 2011-08-28
Hello,

I've been using Ubuntu 11.04 for the past few weeks now and seem to be doing ok with it, however, when I restart or suspend my session and come back on, I notice my screen to be considerably dull. I've done some research and found a command to brighten my screen "sudo setpci -s 00:02 F4.B=E0".. The only problem is, to make my screen bright each time I restart etc I need to use this command. Is there any (simple) way to make it permanent? I'm also quite a newbie.

---

### Post by raja.genupula on 2011-08-28
[https://help.ubuntu.com/11.04/ubuntu-help/display-dimscreen.html](https://help.ubuntu.com/11.04/ubuntu-help/display-dimscreen.html)

---

### Post by Toz on 2011-08-28
For restarts, add the command **setpci -s 00:02 F4.B=E0** to the file **/etc/rc.local** just before the "exit 0" command. Here's how:
[LIST=1]
[*]Open a terminal window
[*]Type in: ```
gksudo gedit /etc/rc.local
```
[*]Add the setpci command before exit 0, like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="Red"]setpci -s 00:02 F4.B=E0[/COLOR]
exit 0

```
[*]Save the file
[/LIST]

For resumes from suspend, we'll do a similar thing but to a different file.
[LIST=1]
[*]In the terminal window again, type in: ```
gksudo gedit /etc/pm/sleep.d/50_brightness
```
[*]Copy/paste the following into the gedit window:
```
#!/bin/bash
case "$1" in
	thaw)
		setpci -s 00:02 F4.B=E0
		;;
esac

```
[*]Save the file and close gedit
[*]Make the file executable:
```
sudo chmod +x /etc/pm/sleep.d/50_brightness
```
[/LIST]

Test it out.

---

### Post by c0dez0r on 2011-09-02
> **Toz said:**
> For restarts, add the command **setpci -s 00:02 F4.B=E0** to the file **/etc/rc.local** just before the "exit 0" command. Here's how:
[LIST=1]
[*]Open a terminal window
[*]Type in: ```
gksudo gedit /etc/rc.local
```
[*]Add the setpci command before exit 0, like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR=Red]setpci -s 00:02 F4.B=E0[/COLOR]
exit 0

```
[*]Save the file
[/LIST]

For resumes from suspend, we'll do a similar thing but to a different file.
[LIST=1]
[*]In the terminal window again, type in: ```
gksudo gedit /etc/pm/sleep.d/50_brightness
```
[*]Copy/paste the following into the gedit window:
```
#!/bin/bash
case "$1" in
    thaw)
        setpci -s 00:02 F4.B=E0
        ;;
esac

```
[*]Save the file and close gedit
[*]Make the file executable:
```
sudo chmod +x /etc/pm/sleep.d/50_brightness
```
[/LIST]

Test it out.

Legend! It works! Thanks a lot!:KS

---

### Post by Toz on 2011-09-02
Glad to hear and thanks for posting back. If you don't mind, can you please mark this thread as solved from the Thread Tools link above so that others can benefit from it as well?

---

