---
title: "Disable user ability to shut down (10.10)"
date: 2011-01-19
forum: General Help
---

### Post by FMDragon on 2011-01-19
Hey guys, just wondering, is there any way to disable a users ability to shutdown a system? I'm setting up a few systems for a teaching lab and we want to disable this feature. I've seen some older (4+ years) tutorials but nothing that would apply to 10.10.
Thanks in advance!

---

### Post by lithopsian on 2011-01-19
Fundamentally, ordinary users don't have the ability to shutdown the system.  The trick is to enable it!  I'm sorry that I don't know for sure the application used for this in 10.10 but you can see easily enough from your menu.  Remove it or change the execute permissions.  That will stop 90% of shutdown attempts.

Then of course you have to make sure that the users don't have any sudo ability.  That will stop almost all the rest.

Now ... have you disabled ACPI response to the power button :)

---

### Post by corncob on 2011-01-19
> **FMDragon said:**
> Hey guys, just wondering, is there any way to disable a users ability to shutdown a system? I'm setting up a few systems for a teaching lab and we want to disable this feature. I've seen some older (4+ years) tutorials but nothing that would apply to 10.10.
Thanks in advance!

You could right-click on the shutdown button and then "remove from panel".  The students might not know they can right-click the panel and then "add to panel..." and put it back on.  In any case, if they really wanted to shut it down they could use the power switch.

---

### Post by corncob on 2011-01-19
> **FMDragon said:**
> Hey guys, just wondering, is there any way to disable a users ability to shutdown a system? I'm setting up a few systems for a teaching lab and we want to disable this feature. I've seen some older (4+ years) tutorials but nothing that would apply to 10.10.
Thanks in advance!

You could right-click on the shutdown button and then "remove from panel".  The students might not know they can right-click the panel and then "add to panel..." and put it back on.  In any case, if they really wanted to shut it down they could use the power switch.

---

### Post by corncob on 2011-01-19
> **FMDragon said:**
> Hey guys, just wondering, is there any way to disable a users ability to shutdown a system? I'm setting up a few systems for a teaching lab and we want to disable this feature. I've seen some older (4+ years) tutorials but nothing that would apply to 10.10.
Thanks in advance!

You could right-click on the shutdown button and then "remove from panel".  The students might not know they can right-click the panel and then "add to panel..." and put it back on.  In any case, if they really wanted to shut it down they could use the power switch.

---

### Post by FMDragon on 2011-01-20
Ah, remove the panel! Never really thought about that. Funny how you try to over complicate an issue and the solution is actually really easy.

The only other issue that I would have would be the 'Shut Down' option in the System menu. Is there anyway to remove that as well? I've tried right click, then edit menus, but that only gives me the ability to remove/edit Preferences, Administration, and Control Center. Doesn't seem to be anything about the rest of the options.

Suggestions?

---

### Post by FMDragon on 2011-01-20
Ah, remove the panel! Never really thought about that. Funny how you try to over complicate an issue and the solution is actually really easy.

The only other issue that I would have would be the 'Shut Down' option in the System menu. Is there anyway to remove that as well? I've tried right click, then edit menus, but that only gives me the ability to remove/edit Preferences, Administration, and Control Center. Doesn't seem to be anything about the rest of the options.

Suggestions?

---

### Post by FMDragon on 2011-01-20
Ah, remove the panel! Never really thought about that. Funny how you try to over complicate an issue and the solution is actually really easy.

The only other issue that I would have would be the 'Shut Down' option in the System menu. Is there anyway to remove that as well? I've tried right click, then edit menus, but that only gives me the ability to remove/edit Preferences, Administration, and Control Center. Doesn't seem to be anything about the rest of the options.

Suggestions?

---

### Post by FMDragon on 2011-01-20
Ah, remove the panel! Never really thought about that. Funny how you try to over complicate an issue and the solution is actually really easy.

The only other issue that I would have would be the 'Shut Down' option in the System menu. Is there anyway to remove that as well? I've tried right click, then edit menus, but that only gives me the ability to remove/edit Preferences, Administration, and Control Center. Doesn't seem to be anything about the rest of the options.

Suggestions?

---

### Post by corncob on 2011-01-21
> **FMDragon said:**
> Ah, remove the panel! Never really thought about that. Funny how you try to over complicate an issue and the solution is actually really easy.

The only other issue that I would have would be the 'Shut Down' option in the System menu. Is there anyway to remove that as well? I've tried right click, then edit menus, but that only gives me the ability to remove/edit Preferences, Administration, and Control Center. Doesn't seem to be anything about the rest of the options.

Suggestions?

I don't seem to have this feature.  No box in front of it that you can uncheck?  Can you select it and press the Delete button? -- or the Properties button and change the command line to something like 'gedit file.txt' where file.txt = "you're not authorized to do this" lol?

---

### Post by matt_symes on 2011-01-21
Hi

One way to stop people shutting down (or rebooting) is to change the policies. This is tested on 10.04 not 10.10 but i think it should still work.

Open a terminal and type

```
sudo nano /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
```

you can change

```
<action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      **<allow_active>yes</allow_active>**
    </defaults>
  </action>
```

to

```
<action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      **<allow_active>no</allow_active>**
    </defaults>
  </action>
```

You can do the same for the reboot section. When i change it on my laptop, if i try to shutdown it will just log me out.

You can disable the power button by typing (if i remember correctly)

```
sudo chmod 0 /etc/acpi/powerbtn.sh
```

You might also want to disable shutdown from the logon screen.

Kind regards

---

