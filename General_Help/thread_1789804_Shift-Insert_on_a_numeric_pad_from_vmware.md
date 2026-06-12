---
title: "Shift-Insert on a numeric pad from vmware"
date: 2011-06-24
forum: General Help
---

### Post by informist on 2011-06-24
Hi, I'm using Ubuntu installed on a vmware virtual machine and everything worked find except accessing Shift-Insert (Shift-0 on the numeric pad) in VMware console window (Windows XP). I'm one of those who used to using Shift-Ins and Ctrl-Ins for clipboard and Insert is where 0 on the numeric pad (Num-Lock is off). With this configuration any Shift-Numeric keys give numbers (as if NumLock was on)

What I noticed:
- The problem is not present if I use TightVNC for Windows for remote access (works as expected)
- The problem doesn't go out if I install open-vm-tools (installed with 
apt-get install --no-install-recommends open-vm-tools
- Vmware console works correctly if the system installed on a virtual machine is Windows

What is the part of the chain that can produce such results?

Thanks

---

### Post by fballem on 2011-06-24
Don't know enough about vmware to know if this helps or not.

In ubuntu, if you use the numeric keypad in the same way that you are used to using it in Windows, then you need to make a change in the keyboard layout.

To do this:
1/ Open the keyboard application. In 11.04, you can open applications and type keyboard. This will open the Keyboard Preferences application.
2/ Once open, select the Layouts tab.
3/ On the Layouts tab, select the Options button.
4/ On the Options menu, select the Miscellaneous Options folder
5/ Make sure that Shift with numeric keypad works as in MS Windows line item is checked. If it is not, check it.
6/ Select Close, which will close the Options menu
7/ Select Close again, which will close the Keyboard Preferences application.

Hope this helps,

---

### Post by informist on 2011-06-24
> **fballem said:**
> Don't know enough about vmware to know if this helps or not.

In ubuntu, if you use the numeric keypad in the same way that you are used to using it in Windows, then you need to make a change in the keyboard layout.

To do this:
...
Hope this helps,

Thanks, I tried this before (forgot to mention), it made things worse for vmware (ctrl-ins stopped coping), but with TightVNC everything worked as before, correctly.

---

### Post by informist on 2011-06-24
I just noticed there there is a special forum about virtualization here. What is the best way to forward this question there? Should I post there linking to this or a moderator can move this topic there? Thanks

---

