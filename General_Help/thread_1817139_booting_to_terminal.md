---
title: "booting to terminal"
date: 2011-08-02
forum: General Help
---

### Post by sIXXvIRUS on 2011-08-02
I have a question..
Is there a way I can boot into terminal rather then booting into the GUI desktop?? Then do a "startx" command if i need to go into the GUI desktop. I am new to linux and thought it would be a VERY GOOD!! hobby to pick up..

Thank You all who view this :-)

---

### Post by sisco311 on 2011-08-02
Hi and welcome to the forums!

Of course you can... See my post here: [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

---

### Post by Kira_Belka on 2011-08-02
2 sisco311 .. it's not polite to send peoples to reading manuals)))

2 sIXXvIRUS ... CTRL+ALT+F1 (for first text terminal) and graphic ALT+F7 to return in GNOME ("GUI")

---

### Post by wojox on 2011-08-02
> **Kira_Belka said:**
> 2 sisco311 .. it's not polite to send peoples to reading manuals)))

2 sIXXvIRUS ... CTRL+ALT+F1 (for first text terminal) and graphic ALT+F7 to return in GNOME ("GUI")

sisco311's response is right on and why rewrite all that when he has an excelent link to refrence? 

Kirca_Belka your showing him the wrong way.

---

### Post by Kira_Belka on 2011-08-02
I think you 're wrong.. if we 'll send peoples to manuals most of them drops idea to use Ubuntu.. do you remember what means in translation word "Ubuntu"? Humanity.
I spent just a second.. and showed sIXXvIRUS easiest way.. just example..if he 's interested more .. he 'll find more info using www or forum.. if he needed just urgent answer he got it.

---

### Post by sisco311 on 2011-08-02
This is a FAQ. I answered it several times. I didn't post a link to manual, but to one of my posts on this forums.

---

### Post by Furball588 on 2011-08-03
heh..and here I'm thinking just adding an init 3 to your boot option in grub would be all you needed.

---

### Post by wojox on 2011-08-03
Your answer Kira the OP will still boot into X and then switch to the  command line.

OP wants to boot straight to X without seeing their desktop or GDM. :D

---

### Post by wojox on 2011-08-03
> **Furball588 said:**
> heh..and here I'm thinking just adding an init 3 to your boot option in grub would be all you needed.

sisco probably has a way to boot to run level 3 and then startx with your .xinitrc. :P

---

### Post by sIXXvIRUS on 2011-08-03
Thank you for your posting to my thread, the only problem i had was:

When I did the "CTRL+ALT+F1" command I came to terminal screen with a PC login prompt. I typed in my normal ubuntu username and password, yet it didnt work. I know its mostly something stupid on my end, but i am sorry being a newbie that why i am on this forum.

---

### Post by sisco311 on 2011-08-03
> **Furball588 said:**
> heh..and here I'm thinking just adding an init 3 to your boot option in grub would be all you needed.

Ubuntu uses Upstart. Upstart is backward compatible with the "old" system V style init daemon, hence runlevels are still emulated but they are kind of obsolete...

Anyway, Debian, as well as most of the distributions based on it, like early Ubuntu, does not make any distinction between runlevels 2 to 5.

---

### Post by Kira_Belka on 2011-08-03
1. Never think that you 're newbie one.. you just 're studying
it's ok
mmmm...
you cann't login?

---

### Post by sisco311 on 2011-08-03
> **sIXXvIRUS said:**
> Thank you for your posting to my thread, the only problem i had was:

When I did the "CTRL+ALT+F1" command I came to terminal screen with a PC login prompt. I typed in my normal ubuntu username and password, yet it didnt work. I know its mostly something stupid on my end, but i am sorry being a newbie that why i am on this forum.

Please post the error message.

---

### Post by sIXXvIRUS on 2011-08-03
there is not an error message i just cant login

---

### Post by sIXXvIRUS on 2011-08-03
**just on a side note**

I only ask about booting into a terminal on ubuntu cause the OS backtrack which is based o ubuntu boots to terminal as well when you start the OS up.

---

### Post by sisco311 on 2011-08-03
> **sIXXvIRUS said:**
> there is not an error message i just cant login

So, what happens after you type in your username and password?

---

### Post by Kira_Belka on 2011-08-03
> **sisco311 said:**
> Please post the error message.

so it seems to me I was right.. and if you 're interested in start/stop X in ubuntu..
as I remember
 
sudo /etc/init.d/gdm stop (or start :) )) 
or 
su 
/etc/init.d/gdm stop

in any terminal)))

---

### Post by sIXXvIRUS on 2011-08-03
login incorrect

---

### Post by Kira_Belka on 2011-08-03
> **sIXXvIRUS said:**
> **just on a side note**

I only ask about booting into a terminal on ubuntu cause the OS backtrack which is based o ubuntu boots to terminal as well when you start the OS up.
you are right about backtrack  it's so

---

### Post by sIXXvIRUS on 2011-08-03
[Kira_Belka]("http://ubuntuforums.org/member.php?u=1367075") speaking of "su" super user commands..
How do i set my super user or (root if it is called that) password? I would rather just do a single sudo su command get into my root account when i want to do a bunch of "apt-get" command in terminal.

---

### Post by Kira_Belka on 2011-08-03
check capital letters in login and "caps lock" indicator..
for example if your user name starts from capital letter..you have to type capital letter in login and etc...

---

### Post by sisco311 on 2011-08-03
> **Kira_Belka said:**
>  
sudo /etc/init.d/gdm stop (or start :) )) 

```

sisco@acme:~/xtmp$ sudo /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm

```


:)

> **Kira_Belka said:**
> 
or 
su 
/etc/init.d/gdm stop


By default the root account is disabled, so you can't use su to become root.

---

### Post by Kira_Belka on 2011-08-03
use sudo

---

### Post by sisco311 on 2011-08-03
> **sIXXvIRUS said:**
> [Kira_Belka]("http://ubuntuforums.org/member.php?u=1367075") speaking of "su" super user commands..
How do i set my super user or (root if it is called that) password? I would rather just do a single sudo su command get into my root account when i want to do a bunch of "apt-get" command in terminal.

Check out: [uhelp]community/RootSudo[/uhelp]

**sudo -i** is the preferred command for starting a root shell.

---

### Post by Kira_Belka on 2011-08-03
is it hard to remove no-login option in gdm for root?)))it's 15 sec)) lol)
and it binds only for graphic terminal emulators) but you can switch to text terminal..so ctrl+alt+f1 and login as root))))

---

### Post by Kira_Belka on 2011-08-03
> **sisco311 said:**
> Check out: [uhelp]community/RootSudo[/uhelp]

**sudo -i** is the preferred command for starting a root shell.

but you 're right sudo is prefered due security reasons

---

### Post by sisco311 on 2011-08-03
> **Kira_Belka said:**
> is it hard to remove no-login option in gdm for root?)))it's 15 sec)) lol)
and it binds only for graphic terminal emulators) but you can switch to text terminal..so ctrl+alt+f1 and login as root))))

Not sure what's your point... Did you read the [thread=1486138]Forum policy on log-in-as-root tutorials[/thread]?

---

### Post by wojox on 2011-08-03
> **sisco311 said:**
> Check out: [uhelp]community/RootSudo[/uhelp]

**sudo -i** is the preferred command for starting a root shell.

Does changing /etc/default/grub to read "text" still work?

---

### Post by sisco311 on 2011-08-03
> **wojox said:**
> Does changing /etc/default/grub to read "text" still work?

It doesn't work in Natty (11.04). The text kernel parameter was a workaround in earlier releases because it wasn't an easy way to disable Upstart jobs. 

In Natty you can use an .override file to disable an Upstart job.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

### Post by Kira_Belka on 2011-08-03
> **sisco311 said:**
> Not sure what's your point... Did you read the [thread=1486138]Forum policy on log-in-as-root tutorials[/thread]?

I red) but it doesn't mean that I cann't login as root when I wanna it))
but being honesty I don't see logic in root graphical login))
sudo is enought)) or sudo bash))))))))))))

---

