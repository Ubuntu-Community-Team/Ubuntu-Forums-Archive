---
title: "lockup during startup"
date: 2010-05-22
forum: General Help
---

### Post by phoenixy on 2010-05-22
Okay, just installed a brand new 10.04

Everything went fine, except internal wireless and usb wireless aren't working. That's somewhat expected.

What I didn't expect though, is that &#65321;&#12288;&#65347;&#65345;&#65358;&#65358;&#65359;&#65364;&#12288;&#65346;&#65359;&#65359;&#65364;&#12288;&#65345;&#65364;&#12288;&#65345;&#65356;&#65356;&#12288;&#65359;&#65358;&#65347;&#65349; I&#12288;&#65345;&#65364;&#65364;&#65349;&#65357;&#65360;&#65364;&#12288;&#65364;&#65359;&#12288;&#65353;&#65358;&#65363;&#65364;&#65345;&#65356;&#65356;&#12288;&#65367;&#65353;&#65362;&#65349;&#65356;&#65349;&#65363;&#65363;&#12288;&#65348;&#65362;&#65353;&#65366;&#65349;&#65362;&#65363;&#12288;&#65288;&#65346;&#65362;&#65359;&#65345;&#65348;&#65347;&#65359;&#65357;&#12288;&#65351;&#65300;&#65299;&#12288;&#65350;&#65359;&#65362;&#12288;&#65364;&#65352;&#65349;&#12288;&#65353;&#65358;&#65364;&#65349;&#65362;&#65358;&#65345;&#65356;&#65356;&#12288;&#65367;&#65353;&#65362;&#65349;&#65356;&#65349;&#65363;&#65363;&#12288;&#65345;&#65358;&#65348;&#12288;&#65358;&#65364;&#65367;&#65362;&#65345;&#65360;&#65360;&#65349;&#65362;&#65291;&#65367;&#65353;&#65358;&#65348;&#65359;&#65367;&#65363;&#65348;&#65362;&#65353;&#65366;&#65349;&#65362;&#12288;&#65350;&#65359;&#65362;&#12288;&#65364;&#65352;&#65349;&#12288;&#65365;&#65363;&#65346;&#12288;&#65359;&#65358;&#65349;&#65289;&#65294;

&#65335;&#65352;&#65349;&#65358; I reboot the system after trying to install wireless driver, I get this watchdog timer message.

```

* Setting sensors limits
BUG: soft lockup - CPU#0 stuck for 61s!

```

And this is in recovery mode. In normal boot mode the system would simply hang at the splash screen.

So what can I&#12288;&#65348;&#65359;&#12288;&#65358;&#65359;&#65367;&#65311;

---

### Post by phoenixy on 2010-05-23
&#65352;&#65349;&#65356;&#65360;:(

---

### Post by bertmanphx on 2010-05-23
Phoenixy,
Try adding "noapic" to the kernel line in Grub, and reboot.

bertmanphx

---

### Post by phoenixy on 2010-05-25
I tried adding noapic to the end of the kernel line. But no, same problem. Still can't boot.

---

### Post by phoenixy on 2010-05-25
the problem has something to do with the startup procedure trying to load the windows wireless usb driver through ntwrapper. They just won't play nice with each other.

---

### Post by phoenixy on 2010-05-27
So is there anything I can do?

---

### Post by bertmanphx on 2010-05-28
Phoenixy,
you could try another addendum to the end of the kernel line:

acpi=force
or
acpi=off

also, you could blacklist the ndiswrapper module....
Can you boot into a different run level?  If so you could remove ndiswrapper using apt, then reboot.

bertmanphx

---

