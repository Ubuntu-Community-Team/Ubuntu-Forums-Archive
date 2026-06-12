---
title: "Help"
date: 2011-05-25
forum: General Help
---

### Post by bearhugs on 2011-05-25
A former employee has removed Windows and put Ubuntu on our back room PC.


This individual has left the area and we are unable to contact him. Our Situation is[LIST=1]
[*]No Admin Rights
[*]No Desktop Icons
[*]No Firefox Browser Icon.
[*]We must access internet thru recyle bin "get help online"[/LIST]

---

### Post by iclestu on 2011-05-25
Guess he can't expect a reference anytime soon :p .... im sure someone will come along to help in a min but I couldnt resist!

---

### Post by deserthowler on 2011-05-25
> **bearhugs said:**
> [FONT=Book Antiqua][SIZE=2]A former employee has removed Windows and put Ubuntu on our back room PC.[/SIZE][/FONT]
 
[FONT=Book Antiqua][SIZE=2]This individual has left the area and we are unable to contact him. Our Situation is[/SIZE][/FONT][LIST=1]
[*][FONT=Book Antiqua][SIZE=2]No Admin Rights[/SIZE][/FONT]
[*][FONT=Book Antiqua][SIZE=2]No Desktop Icons[/SIZE][/FONT]
[*][FONT=Book Antiqua][SIZE=2]No Firefox Browser Icon. [/SIZE][/FONT]
[*][FONT=Book Antiqua][SIZE=2]We must access internet thru recyle bin "get help online"[/SIZE][/FONT]
[/LIST]

Not sure but do you have important data there?  If not, the easiest fix is to either do a fresh install of Windows or Ubuntu.  If Ubuntu, probably 10.04.

Earl

---

### Post by nothingspecial on 2011-05-25
> **bearhugs said:**
> [FONT=Book Antiqua][SIZE=2]A former employee has removed Windows and put Ubuntu on our back room PC.[/SIZE][/FONT]
 

[FONT=Book Antiqua][SIZE=2]This individual has left the area and we are unable to contact him. Our Situation is[/SIZE][/FONT][LIST=1]
[*][FONT=Book Antiqua][SIZE=2]No Admin Rights[/SIZE][/FONT]
[*][FONT=Book Antiqua][SIZE=2]No Desktop Icons[/SIZE][/FONT]
[*][FONT=Book Antiqua][SIZE=2]No Firefox Browser Icon. [/SIZE][/FONT]
[*][FONT=Book Antiqua][SIZE=2]We must access internet thru recyle bin "get help online"[/SIZE][/FONT]
[/LIST]

Well you could reinstall windows, however,

If you would like admin rights do this

Restart the computer, hold down shift to bring up the boot options.

Choose recovery mode (root shell) or what ever they call in your version.

Type

```
adduser <username> admin
```

Change that for the username you are logged on as.

Then

```
exit
```

---

### Post by LordNeo on 2011-05-25
Backup all important data (and probably the home folder completly) then do a reinstall and then copy over the home folder and the data.

Another thing to try could be to boot from a live cd and then replace the password file (and shadow also) adding the guest user from the live cd (basically, copy the line of the user, from the cd to the old fs)

---

### Post by bearhugs on 2011-05-25
Agree on fresh install, however he has locked out download rights.

---

### Post by Telengard C64 on 2011-05-25
Are you sure Windows was completely removed? It is usually possible to [dual boot](http://en.wikipedia.org/wiki/Dual_boot) Ubuntu with Windows.

Do you see the [Grub menu](http://en.wikipedia.org/wiki/GNU_GRUB) when you boot the computer? If not then you may try pressing the **Esc**ape key when booting to show the menu. If you see the Grub menu then you should be able to choose Windows from there.

Even if Windows is not shown in the Grub menu, that does not necessarily mean Windows was removed. It might simply mean that Windows was not added to the Grub menu.

All the situations described above are fixable. Just provide enough details about your situation so we can help.

If Windows really was deleted from the computer, then that cannot be fixed. In such a case you really only have two options.

[list=1]
[*]Reinstall Windows
[*]Learn to use Ubuntu
[/LIST]

If you want option #1, then you'll need your Windows installation disc.

If you want option #2, then please consider starting at one of these fine resources.

[list]
[*][Official Ubuntu Documentation and Community Help Pages](https://help.ubuntu.com/)
[*][Unofficial Free Ubuntu Manual For Users](http://ubuntu-manual.org/)
[*][Ubuntu Pocket Reference](http://www.ubuntupocketguide.com/index_main.html)
[*][UbuntuGuide for customization](http://ubuntuguide.org/)
[/list]

HTH

---

### Post by LordNeo on 2011-05-25
> **bearhugs said:**
> Agree on fresh install, however he has locked out download rights.
try to get to a console (ALT+F2 perhaps?) and then try using wget

---

