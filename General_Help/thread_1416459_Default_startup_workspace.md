---
title: "Default startup workspace"
date: 2010-02-26
forum: General Help
---

### Post by jon.mithe on 2010-02-26
Hi,

Is there a way to change which workspace is selected on starting gnome / ubuntu?

I.e. on starting it always starts on the first workspace.  Given I have multiple workspaces, it would be handy for it to start in the middle one (I keep on starting up, opening apps then have to move them to the other workspace :P)

I get the feeling this is a 1 line edit in a configuration file, but I'm struggling to find out where.

Thanks, jon

---

### Post by Monkey of Rage on 2010-08-01
bump, I've also been on the hunt for a solution to this same question, with absolutely no luck.

---

### Post by prodigy_ on 2010-08-01
You can install **wmctrl**: ```
sudo aptitude install wmctrl
``` and then add a launcher to Startup Applications (System/Preferences/Startup Applications) with a command like: ```
wmctrl -s <workspace>
``` where <workspace> is some number. The first workspace is 0, the second is 1, etc.

This probably won't work if you have Visual Effects enabled because Compiz combines all workspaces into one.

---

### Post by Monkey of Rage on 2010-08-02
I was curious if it's possible to edit something in the Configuration Editor, or if needed; add a 'New Key', in order to choose which workspace to boot to.

---

### Post by vbabiy on 2010-08-11
Has any one been able to get this to work?

---

### Post by wik+ on 2011-02-20
> **vbabiy said:**
> Has any one been able to get this to work?

Yep, for compiz you might need to add few more tricks:
[http://askubuntu.com/questions/20399/position-at-center-workspace-when-login](http://askubuntu.com/questions/20399/position-at-center-workspace-when-login)

p.s.
I've 3 horizontal workspaces and here is my steps to make center default:

 * switch to workspace you want to make default
 * open terminal
 * execute: wmctrl -d
 * output will be something like this:
   0  * DG: 4098x768  **VP: 1366,0**  WA: 0,24 1366x744  Workspace 1
 * you can use VP values to switch to current workspace, e.g.:
   wmctrl -o 1366,0

That's it, now add wmctrl to your startup script and you're done.

---

