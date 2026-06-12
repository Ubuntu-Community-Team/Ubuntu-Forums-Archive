---
title: "Can't change certain things when logged in via remote xession"
date: 2009-12-21
forum: General Help
---

### Post by nullsmack on 2009-12-21
I just updated to 9.10 and something that worked before doesn't anymore. I use my ubuntu computer over a remote x-session a huge majority of the time. I only use the local login when I can't login remotely. The computer is sitting right next to me, but I still use a remote x-session so I don't need to switch my monitor over constantly and it works perfectly.  Except since I updated it refuses to let me mount any drives remotely over the same session. I can log into the local console and it works fine! I'm guessing this is a similar security setting that prevents me from changing settings in the "Users and Groups" menu over a remote session.  I'm fine with that but I must be able to mount or unmount drives over my xsession. Where is the config file I need to text edit to change this setting?

---

### Post by nullsmack on 2009-12-21
Just trying some stuff. I edited /etc/gdm/custom.conf and set RelaxPermissions=2 under [security] and that didn't change anything. I'm guessing it has nothing to do with gdm?

---

### Post by TsarBomba on 2009-12-21
Sorry, I don't have an answer, but here are a couple thoughts:

Do you mean that you're using rdesktop, vnc, nx, or something like that?  And some gui-based mounting program?  If you login remotely with [FONT=Courier New]ssh -Y myhost[/FONT] and use the [FONT=Courier New]mount[/FONT] and [FONT=Courier New]umount[/FONT] commands, it should work exactly as when you login locally.

Regarding the use of another computer right next to your main box, I love [FONT=Courier New]x2x[/FONT].  Say myhost is your ubuntu box sitting to your left and running sshd.  Run this command on your main box:

```
ssh -Y myhost x2x -west -to :0
```and when you move the mouse to the left side of the screen on your main box control from both your mouse and keyboard will jump over to myhost.

(If it's on the other side, use -east, ...)

Back to your original problem, what exactly is the command/program you're running and what is the exact error message?

---

### Post by nullsmack on 2009-12-21
I'm using xdmcp. I can use an X server called "Xming" running on my windows computer to remotely login. When it starts up, I get the exact same GDM login screen as if I'm using a monitor, keyboard and mouse connected right to the computer.  Apparently the devs have decided to kill off much of the support for this operation. [http://www.peppertop.com/blog/?p=671](http://www.peppertop.com/blog/?p=671) I found this blog while looking for information to solve my problem. It used to be possible to set this stuff up in a gui, but now it requires mucking about in text files.  I already have XDMCP working, I've been running it forever. My error message that I'm getting is simply this "Unable to mount 'hdd name'  Not Authorized". I _only_ get this error when I am logged in remotely. I can log into the exact same user in the "local" console and it will happily mount any drive I want it to.  I don't need to change the way I'm logging in. I only need to change the permissions. Ubuntu is awesome but not when it tells me I'm not authorized to do stuff on my own computer.

EDIT: bug report is apparently in about the XDMCP problem [https://bugs.launchpad.net/gdm/+bug/408417](https://bugs.launchpad.net/gdm/+bug/408417) I already have XDMCP working, so this doesn't apply to me. I just need to figure out what permissions change just because I'm logged in via XDMCP rather than the local graphic console.

---

