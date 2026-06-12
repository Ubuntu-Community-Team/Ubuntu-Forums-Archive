---
title: "Password Everytime?"
date: 2010-03-12
forum: General Help
---

### Post by kgw on 2010-03-12
I am playing with Ubuntu and found a really annoying feature. Every time I open the software center (Or some other programs) I have to enter my password. This gets extremely annoying and redundant. Is there a way to get rid of that feature? I am the only person that uses my computer and find it unnecessary.
How can I kill that?

---

### Post by Enigmapond on 2010-03-12
As annoying as it may be to you, this is part of what's keeping your computer safe. To run it as root all the time is very dangerous and not advisable and unfortunately, no one here will be able to advise you on how to do this. It's just the way Ubuntu works.

---

### Post by kgw on 2010-03-12
I understand that but there is a fine line between "Security and Paranoia".

This is a Fresh Install of Ubuntu. I am installing packages and like every third one I have to type in a password again. From what I understand Ubuntu doesn't have a SU account so I can't use that to get everything installed and setup then create sub accounts without SU access.

---

### Post by sdpiowa on 2010-03-12
Ubuntu DOES have a root account, but it's disabled by default.  I highly recommend not using it, as it could seriously compromise your security.

---

### Post by matrix14 on 2010-03-12
Little advise (but better to not try it!):

Add this on your /etc/sudoers :

```

%[your_login_name]= NOPASSWD: [/list/to/path/of/program/here]

```

That will lead certain programs those usually needs password to no need again, but only for your account. 
But please I suggest once to not try this unless you know what to do.

---

### Post by cjhabs on 2010-03-12
> **kgw said:**
> I understand that but there is a fine line between "Security and Paranoia".

This is a Fresh Install of Ubuntu. I am installing packages and like every third one I have to type in a password again. From what I understand Ubuntu doesn't have a SU account so I can't use that to get everything installed and setup then create sub accounts without SU access.

You control this via /etc/sudoers:
```

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

```

I had done this but undid it after a while after reading about viruses and Linux. While they are a minor issue, running a compromised program with elevated privelidges can mess up your system, so I decided I would rather enter my password to be aware of when I was running anything with those elevated privelidges.

---

### Post by coffeecat on 2010-03-12
> **kgw said:**
> I am playing with Ubuntu and found a really annoying feature. Every time I open the software center (Or some other programs) I have to enter my password.

When using MacOS I encounter a really annoying feature. Whenever I download a dmg to install an app, I have to enter my password before the system will install it.

When using Vista or Windows 7 I encounter a really annoying feature. Whenever I download an app installer and double-click I have to "allow" through UAC.

:wink:

I can circumvent both, just as I can circumvent the Ubuntu security model, but the authorisation is there for a purpose. To help protect **your** system.

---

### Post by kgw on 2010-03-12
Understood. Now if I change the wallpaper is the CIA going to break into my house and water board me?

Issue:
Open USC, add password. Install program or two. Have to add password again even though I am still in USC. Install program, Add password to install program.

How about
Open USC and add password
Add Programs without repeating passwords.
Close USC

Next time you open USC, add password again.

I have nothing against Ubuntu. The Software is nice and it doesn't appear to be bloated. But this password adding every couple of minutes when YOUR IN THE PROGRAM, isn't security, it's annoying.

---

### Post by stoneage on 2010-03-12
The default timeout is 15 minutes. You can extend that if you wish, but I would urge caution. Fair enough if you are the only person near your machine, but the point of it is if your machine is compromised in any way you don't leave the door open for someone else to do as they please with your root session.

Is it really too much trouble to enter some text every once in a while?

---

### Post by kgw on 2010-03-12
> **stoneage said:**
> The default timeout is 15 minutes. You can extend that if you wish, but I would urge caution. Fair enough if you are the only person near your machine, but the point of it is if your machine is compromised in any way you don't leave the door open for someone else to do as they please with your root session.

Is it really too much trouble to enter some text every once in a while?

OK cool. How do I extend that limit (As mine happens about every two minutes).

And no, it's not any trouble adding a passcode now and then, I have NO issue with that. As a matter of fact, thats what I love about linux distro's, the security.

---

### Post by sisco311 on 2010-03-12
> **kgw said:**
> OK cool. How do I extend that limit (As mine happens about every two minutes).

And no, it's not any trouble adding a passcode now and then, I have NO issue with that. As a matter of fact, thats what I love about linux distro's, the security.

USC uses policykit & NOT sudo/gksu. As far as I know, policykit's timeout is hard-coded and  can't be changed, however you can disable the password authentication requirement for installing software.

I'm installing Ubuntu right now (long story...). If you wish I can post instructions in a few minutes.

---

### Post by stoneage on 2010-03-12
> **sisco311 said:**
> USC uses policykit & NOT sudo/gksu. As far as I know, policykit's timeout is hard-coded and  can't be changed, however you can disable the password authentication requirement for installing software.

Would that be System -> Preferences -> Startup Applications then disable PolicyKit Authentication Agent?
Unfortunately that can cause Software Centre to malfunction - [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/499937](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/499937)

Why not install through Synaptic or CLI, then you get your 15 minute minimum, or you can browse in Synaptic as long as you want and install all of them together. Click on Sections, then browse Games and Amusement(or whatever), select what you want to install and Apply when you are done.

---

### Post by sisco311 on 2010-03-12
> **stoneage said:**
> Would that be System -> Preferences -> Startup Applications then disable PolicyKit Authentication Agent?
Unfortunately that can cause Software Centre to malfunction - [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/499937](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/499937)


Nope, the Authentication Agent provides the authentication dialog, without the dialog you can't authenticate yourself as an admin.

@OP,in order to disable the password requirement in USC, you have to edit the /usr/share/polkit-1/actions/org.debian.apt.policy file:
```
gksu gedit  /usr/share/polkit-1/actions/org.debian.apt.policy
```

and in the [COLOR="Red"]org.debian.apt.install-packages[/COLOR] entry change the authentication mode from **auth_admin_keep** to **yes**.


```

...
  <action id="[COLOR="Red"]org.debian.apt.install-packages[/COLOR]">
    ...
    <description xml:lang="en_GB">Install packages</description>
    ...
    <message xml:lang="en_GB">Authentication is required to install software packages</message>

    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>

...

```

---

### Post by NertSkull on 2010-03-12
> **kgw said:**
> OK cool. How do I extend that limit (As mine happens about every two minutes).


Its been a while.  But I believe you can change the password timeout in the sudoers file.

```
sudo visudo
```

Then find the password time out, and change it to what you want.  I think if you put it as 0 it never will timeout.

You may have to add the line if its not in there.  I think its something like 

```
Defaults syslog=auth,passwd_timeout=10
```

You've heard the security risks already, so I won't comment there.

---

### Post by sisco311 on 2010-03-12
> **NertSkull said:**
> Its been a while.  But I believe you can change the password timeout in the sudoers file.

```
sudo visudo
```

Then find the password time out, and change it to what you want.  I think if you put it as 0 it never will timeout.

You may have to add the line if its not in there.  I think its something like 

```
Defaults syslog=auth,passwd_timeout=10
```

You've heard the security risks already, so I won't comment there.

passwd_timeout sets the number of minutes before the sudo password prompt times out. 

0 means never expire (wait until the password is provided)
 
timestamp_timeout controls the number of minutes that can elapse before sudo will ask for a passwd again.

0 means *always prompt*,
a negative value means *never expire*.

In Ubuntu, the default timestamp is set to 15 minutes. I wouldn't change it to higher value.

NOTE: sudo's timestamp has nothing to do with policykit's timestamp.

---

