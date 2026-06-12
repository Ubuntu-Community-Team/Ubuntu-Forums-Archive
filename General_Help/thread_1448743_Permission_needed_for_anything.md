---
title: "Permission needed for anything"
date: 2010-04-07
forum: General Help
---

### Post by gameguy on 2010-04-07
I am the first user created under ubuntu. Therefore I am administrator. Yet it still keeps asking me for my password to do many things, even like restarting. I don't want it to ask me; I want it to shut down without me typing in a password, for example.

---

### Post by mikewhatever on 2010-04-07
In Ubuntu, and many other distros, the administrator also runs without admin privileges. You can easily shut down the computer by clicking the power icon in the top right corner of the screen and selecting *Shut Down*. No password should be required.
These permissions are an integrated part of Linux, and is one of the reasons why Linux is much more secure.

---

### Post by dominiquec on 2010-04-07
It's a feature, not a bug. :-)

Generally, things that involve system administrator levels will ask for your password (within a specified time period.)

---

### Post by gameguy on 2010-04-07
Is there any way to disable this "feature". And shutting down isn't the only thing which asks for a password.

---

### Post by dominiquec on 2010-04-07
Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

### Post by mikewhatever on 2010-04-07
> **gameguy said:**
> Is there any way to disable this "feature". And shutting down isn't the only thing which asks for a password.

If you have to ask, then no. As said, shutting down shouldn't require a password.

---

### Post by mikewhatever on 2010-04-07
> **dominiquec said:**
> Log in as root.  Not recommended, though, but if that's the way you want to roll....

Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) first.

Check this out: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201).

---

### Post by gadolinio on 2010-04-07
How strange... Shuting the computer down is not something that requires special permissions... It's not like installing software; it's just turning the computer off!!

Try this: system--> administration--> authorizations.
You'll see a list of actions on the left, and who can perform each one on the right. You'll be asked for your password to modify those things, but hopefully not anymore after that!
Hope you find this useful...

---

### Post by gameguy on 2010-04-07
I use 9.10 and authorizations isn't displayed there. Would it be under another name?

---

### Post by gadolinio on 2010-04-07
> **gameguy said:**
> I use 9.10 and authorizations isn't displayed there. Would it be under another name?

Mmmm try pressing Alt F2, then type "polkit-gnome-authorization", hit enter.

---

### Post by skillllllz on 2010-04-07
Something is not right, it should not ask you for your password to shutdown the computer. Are you shutting down from the command line?

---

### Post by gameguy on 2010-04-07
Tried, Didn't work. Typed into terminal, said that it needed to be installed. Installed it and now don't know what to do with it.

---

### Post by doas777 on 2010-04-07
i disagree, shutdown should require admin if another user is still logged in. this is at heart a multi-user system after all. if you are the only one though, it should just go through.

---

### Post by gameguy on 2010-04-07
> **skillllllz said:**
> Are you shutting down from the command line?

No.

---

### Post by gameguy on 2010-04-07
Single user system

---

### Post by gameguy on 2010-04-07
Sometimes it works and sometimes it doesn't.

---

### Post by sisco311 on 2010-04-07
> **doas777 said:**
> i disagree, shutdown should require admin if another user is still logged in. this is at heart a multi-user system after all. if you are the only one though, it should just go through.

That's the default, I don't know why is not working for the OP.


@OP: Please post the content of the /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy file:
```
cat /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
```

---

### Post by scottuss on 2010-04-07
> **gameguy said:**
> Sometimes it works and sometimes it doesn't.

You definitely only have 1 user account?

What do you see under System > Administration > Users and Groups ?

---

### Post by SoFl W on 2010-04-07
Are two users logged in at the same time?  Perhaps you are also logged in with a guest account?

---

### Post by gameguy on 2010-04-07
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">

<!--
Policy definitions for ConsoleKit
-->

<policyconfig>

  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.stop-multiple-users">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart">
    <description>Restart the system</description>
    <message>System policy prevents restarting the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart-multiple-users">
    <description>Restart the system when multiple users are logged in</description>
    <message>System policy prevents restarting the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

</policyconfig>

and about the user account:
I have Matt and root

---

### Post by gameguy on 2010-04-07
No guest

---

### Post by SoFl W on 2010-04-07
Are the other users logged out?  Are all terminal windows closed?  Are all applications closed?

---

### Post by gameguy on 2010-04-07
No other users. Terminal windows often open. I often use sudo/su - if that has anything to do with it.

---

### Post by sisco311 on 2010-04-07
If you want to be able to stop/restart the system, without being prompted for a password, even if when multiple users are logged in, then edit the file:
```
gksu gedit /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
```
and change the authentication mode from *auth_admin_keep* to *yes*:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">

<!--
Policy definitions for ConsoleKit
-->

<policyconfig>

  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.stop-multiple-users">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart">
    <description>Restart the system</description>
    <message>System policy prevents restarting the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart-multiple-users">
    <description>Restart the system when multiple users are logged in</description>
    <message>System policy prevents restarting the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>

</policyconfig>

```

---

### Post by mick222 on 2010-04-07
If you use "sudo shutdown now" you need to input the password . If all terminal windows are closed and you use the shutdown button, unless other users are logged in it should shutdown without the password.

---

### Post by Calash on 2010-04-07
The short and simple answer is:

If you are using the shutdown button in the menu and you are sure there are no other users connected to your system and it asks you for a password then something is wrong with your system.

---

### Post by SoFl W on 2010-04-07
> **gameguy said:**
> No other users. Terminal windows often open. I often use sudo/su - if that has anything to do with it.


Bingo!  In a terminal window with sudo you are still logged in as an admin, you need admin's permission to close admin's privileges, and shut down the system.

---

### Post by skillllllz on 2010-04-07
> **calash said:**
> the short and simple answer is:

If you are using the shutdown button in the menu and you are sure there are no other users connected to your system and it asks you for a password then something is wrong with your system.

+1

---

### Post by gameguy on 2010-04-11
It's not just that. It asks me for everything. I want to enable the root account. I don't want to be protected from myself. I do backups, have antivirus, secure password, firewall. And I don't have any private info on my computer.

---

### Post by sisco311 on 2010-04-11
> **gameguy said:**
> It's not just that. It asks me for everything. I want to enable the root account. I don't want to be protected from myself. I do backups, have antivirus, secure password, firewall. And I don't have any private info on my computer.

We can't help with that:
[thread=716201]Forum policy on log-in-as-root tutorials[/thread]

---

### Post by gadolinio on 2010-04-11
> **sisco311 said:**
> We can't help with that:
[thread=716201]Forum policy on log-in-as-root tutorials[/thread]

Wow, didn't know about that. I was just about to post a howto... haha. 
I've read the link, and definitely, it is sensible. Thanks for posting it.


> **gameguy said:**
> Tried, Didn't work. Typed into terminal, said that it needed to be installed. Installed it and now don't know what to do with it.

So you can open it? If you can, you'll see a list of actions on the left, and when you click on any of them, the right side of the window shows who can perform that action, and if authentication is needed. Click the edit button, and set what you want. For example, for shutdown i have the following: anyone--> no ;  console --> no  ; active console --> yes.
Hope you find this useful...

---

### Post by aysiu on 2010-04-11
> **sisco311 said:**
> We can't help with that:
[thread=716201]Forum policy on log-in-as-root tutorials[/thread]
To gameguy, please read what sisco311 posted.

If you still have *specific* questions, post a new thread.

---

