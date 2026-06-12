---
title: "Run Program before/in place of GNOME??"
date: 2006-05-30
forum: General Help
---

### Post by featherking on 2006-05-30
Hello all,

I was wondering if this is possible. I would like to have a program run and no other programs. This computer will be placed in a public place and i was wondering if it were possible to just have it run a program instead of loading up a desktop. In windows this can be accomplished by replacing the shell 'explorer.exe' to whatever program you like. Is there a similar function in Ubuntu?

I want the users to use this program only.

Thanks

---

### Post by hw-tph on 2006-05-31
Edit the ~/.xsession file and set GDM to start a "Custom session". To just run one program, put it on a single line after an exec statement:
```
exec /usr/local/bin/myprogram
```
*exec* makes the specified program actually replace the running script so when this program exits, the X session will be over.

Consider my Openbox .xsession script:```
export LC_ALL=sv_SE &
wmnetload &
wmacpiload &
wmmemload &
wmcpuload &
urxvtd &
pypanel &
exec openbox
```
Lines ending with an ampersand ("&") make the commands detached and the script just moves on to the next line without waiting for the commands to finish. When the last line is executed the script process will be replaced by the openbox process. When Openbox exits, everything else will quit too and the session is over.


Håkan

---

### Post by featherking on 2006-05-31
Okay that worked fine i also read the [CustomXScript]("http://wiki.ubuntu.com/CustomXSession") wiki page. Very Informative.

However, i have another question. Can you have the session end with a command also? In my case i want to load straight into a program (which works fine with .xsession) but when the program is done i want the computer to shutdown. Right now when i quit the program it goes back to the login screen instead of shutting down the whole computer.

EDIT: The problem is -> the program is supposed to run /usr/sbin/poweroff but this command must be run as root. Is there a way to start the exec as sudo without requiring password?

---

### Post by trorion on 2006-05-31
Alternatively is it possible to allow shutdown by anyone?  I know it can be done in some way because I don't need to sudo to shutdown in gui mode...

---

### Post by featherking on 2006-05-31
Ive tried chmod a+rwx /sbin/poweroff and chmod a+rwx /sbin/halt to no avail. It still says "poweroff: must be superuser". Then i tried chown-ing the files and again to no avail.

---

### Post by featherking on 2006-05-31
Found the solution:

sudo chmod u+s /sbin/[your_command_here]

So in my case i wanted to be able to run poweroff as any user so i type in terminal

```
sudo chmod u+s /sbin/poweroff
``` and voila! now i can just type poweroff and the system goes down (poweroff=halt or shutdown -h now)

-later

---

