---
title: "gnome-terminal looped (how to reset it's profile?)"
date: 2009-08-18
forum: General Help
---

### Post by cyprys on 2009-08-18
Hi.

I've just did something stupid:

gnome-terminal profile settings -> default profile -> run a custom command instead of my shell: "gnome-terminal --full-screen"

Well. It didn't come out like I wanted - wonder why... Gnome-terminal runs itself recursively until it overflows some buffer then some instance crashes (killing all the child threads) and the whole process starts all over again and again.
...I'm kind of proud of myself!

**How to reset the gnome-terminal's default profile?**

I tried to find the correct configuration file but all I've found is:
/home/eddy/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml

and changing this xml doesn't do anything - running the terminal puts back "true" into the following line:

<entry name="use_custom_command" mtime="1250632362" type="bool" value="true"/>

Any ideas where to find the correct .conf file?

Cheers,
Cyprian

---

### Post by DaithiF on 2009-08-18
Hi,
Alt-F2, run gconf-editor
navigate to apps -> gnome-terminal -> profiles -> default, and uncheck the use_custom_command checkbox.

---

### Post by cyprys on 2009-08-18
Thank you! :)

edit:
[SOLVED]

---

### Post by collymoore on 2011-05-04
well i'm having almost the same problem but it differs on that by mistake I replace the commands that perform the ctrl+ c "which cancel something on the shell" and now it just copy and paste. how can i make it go back to default to the previous shift + ctrl + c to copy and ctrl + c to cancel!??:confused:

---

### Post by cyprys on 2011-05-04
> **collymoore said:**
> well i'm having almost the same problem but it differs on that by mistake I replace the commands that perform the ctrl+ c "which cancel something on the shell" and now it just copy and paste. how can i make it go back to default to the previous shift + ctrl + c to copy and ctrl + c to cancel!??:confused:

Before I reply let me note you shouldn't dig up old posts, especially marked as SOLVED, and append your question at the end - even if it's related. It is far better to create a new topic and point to the solved thread in there adding a short summary of your version of the problem.

Regarding your question, solution depends on what stty driver you use, what terminal, graphical session manager, etc.

You might have changed some options of **konsole** (if this is the terminal you use) as described here: [[link]](http://www.linuxquestions.org/questions/linux-software-2/change-bash-shortcut-keys-such-as-ctrl-c-818170/).

You also may be using some script which traps C-c combination.

Check your **.bashrc**, **.profile** and **.initrc** files for key bindings.

Other than that create a new user, login with its authentication data and check out its shell. If it works with new user account the problem lies in your *$HOME* settings and you can probably delete those safely (defaults from /etc should be used instead and you can reconfigure your profile).

Also check your **bind -P** for *\C-c* combination.

I'm just spamming ideas here. Maybe something will lead you to more helpful reading material.

---

