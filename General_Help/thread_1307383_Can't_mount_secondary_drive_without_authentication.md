---
title: "Can't mount secondary drive without authentication"
date: 2009-10-31
forum: General Help
---

### Post by llib1234 on 2009-10-31
Hi,

I'm using ubuntu 9.10 karmic final release and I have to always authenticate (using password) everytime I boot up and try to mount my other hard drive partitions.

Do you know how to get rid of this?

---

### Post by mc4man on 2009-10-31
If you're referring to a partition(s) that **isn't automounted** at boot (fstab entry) then there is a easy workaround till a means is provided to set.

```
gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

```

In the 2nd section replace the blue as shown. (just replace, don't mess with formatting

orig 
 ```
<action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]auth_admin_keep[/COLOR]</allow_active>
    </defaults>
  </action>

```
edited
  ```
 <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]yes[/COLOR]</allow_active>
    </defaults>
  </action>
```

you then should be able to mount from 'places' without password

some edits in post 5 you should glance at.

[http://ubuntuforums.org/showthread.php?t=1299820](http://ubuntuforums.org/showthread.php?t=1299820)

---

### Post by llib1234 on 2009-11-01
Thanks mate!

Works perfectly. 
Just wish ubuntu made it like this in the first place

---

### Post by krishnab108 on 2009-11-01
> **mc4man said:**
> If you're referring to a partition(s) that **isn't automounted** at boot (fstab entry) then there is a easy workaround till a means is provided to set.

```
gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

```In the 2nd section replace the blue as shown. (just replace, don't mess with formatting

orig 
 ```
<action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR=Blue]auth_admin_keep[/COLOR]</allow_active>
    </defaults>
  </action>

```edited
  ```
 <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR=Blue]yes[/COLOR]</allow_active>
    </defaults>
  </action>
```you then should be able to mount from 'places' without password

some edits in post 5 you should glance at.

[http://ubuntuforums.org/showthread.php?t=1299820](http://ubuntuforums.org/showthread.php?t=1299820)

Hi Thanks... This solved my problem too... working fine......

---

### Post by dynaman on 2009-11-03
thanks thats another one of those irritations sorted out:p

---

### Post by vijay_uforum on 2009-11-05
Thanks

---

### Post by stinkeye on 2009-11-06
--

---

### Post by GillesD on 2009-11-18
[COLOR=Black]Thanks for the info :) I got it sorted now. 

Btw, if I change all the "auth_admin_keep" to "yes", will that be harmful? It's a regular desktop home computer so I take it there won't be many security risks?[/COLOR]

---

### Post by kabra.anuj on 2009-11-25
Thanks.
I am new to ubuntu and found this really helpful.

---

### Post by ykasidit on 2010-01-11
Thanks! Solved the xubuntu 9.10 gigolo mount problem! :D

---

### Post by Qbert on 2010-01-20
Thanks

---

### Post by Eredeath on 2010-01-30
Thank you! You've earned this: :KS :KS :KS :KS :KS :KS :KS :KS

---

### Post by BobCFC on 2010-02-05
mc4man \\:D/ :popcorn: \\:D/

---

### Post by Endolith on 2010-04-02
How do we get the old behavior of auto-mounting external drives at startup?  This new authentication is really annoying.

---

### Post by whittaker007 on 2010-04-03
mc4man answered this question in the second post in this thread. But if you're asking why it's not the Ubuntu default anymore, I can only assume that it's for security so that unauthorized parties can't gain access to your attached drives. But I also think it ought to have a gui app to manage these security preferences, and that should be an optional step in the Ubuntu install wizard.

---

### Post by Endolith on 2010-04-03
> **whittaker007 said:**
> mc4man answered this question in the second post in this thread.

No, that post describes how to allow users to mount drives without entering a password.

> **whittaker007 said:**
> But I also think it ought to have a gui app to manage these security preferences, and that should be an optional step in the Ubuntu install wizard.

Yes.

---

### Post by whittaker007 on 2010-04-03
Ah of course. Fortunately there is a gui app for that. On my version of Ubuntu (Linux Mint) the program is called Storage Device Manager. If you don't have that there is a pretty much identical app called Pysdm which you can install with your package manager.

These programs list all the drives currently connected to your machine and has an assistant wizard which lets you choose whether it gets mounted at boot time, and various permissions around who can access, mount and unmount the drives.

It's possible this app might actually get around the original problem with the checkbox for "Allow any user to mount the filesystem", but since I have the first fix already in place, I can't test it.

---

### Post by rpinwelly on 2010-04-19
Thank you; fixed my problem as well.1 :)

---

### Post by amsterdamharu on 2010-04-25
Great, thanks.

I was looking into the groups and what member I need to be off to mount in nautilus without password. That would be the most logical way to do it for me. Now any user can mount local drives and partitions.

It could be solved maybe by editing the fstab and entering the partitions/drives you want only certain users to mount but as far as I know it only has user and nouser options not specific users and groups.

I have to look further into that xml policy file maybe the answer is in there but right now I am happy not to see that annoying password dialogue pop up every time.

---

### Post by rastar101 on 2010-09-12
mine was in "/usr/share/polkit-1/actions/org.freedesktop.udisks.policy "
bu the rest was the same!!
thanx!
it solved my problem!

---

### Post by jamesisin on 2010-09-12
This sounds like a solved thread.  Could the OP mark it as such?

---

