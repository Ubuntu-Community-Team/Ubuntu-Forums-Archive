---
title: "How to mount hard disk partitions"
date: 2010-02-26
forum: General Help
---

### Post by raunhar on 2010-02-26
I am using Ubuntu 9.10
Till 9.04, I never had to authenticate while mounting the partitions of my PC hard disk (there are three partitions)
after upgarding to 9.10, everytime I need to mount the partitions, I have to authenticate.
What is the way that the authentication gets remembered.

---

### Post by sisco311 on 2010-02-26
Edit the /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy file:
```
gksu gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy
```
in the [COLOR="Red"]org.freedesktop.devicekit.disks.filesystem-mount-system-internal[/COLOR] entry change the authentication mode from **auth_admin_keep** to **yes**:
```
...
  <action id="[COLOR="Red"]org.freedesktop.devicekit.disks.filesystem-mount-system-internal[/COLOR]">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**auth_admin_keep**</allow_active>
    </defaults>
  </action>
...

```
-->
```
...
  <action id="[COLOR="Red"]org.freedesktop.devicekit.disks.filesystem-mount-system-internal[/COLOR]">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**yes**</allow_active>
    </defaults>
  </action>
...

```

---

### Post by raunhar on 2010-02-26
Thanks. It was done.

---

