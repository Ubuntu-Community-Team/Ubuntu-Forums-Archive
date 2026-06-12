---
title: "BIOS password"
date: 2011-06-01
forum: General Help
---

### Post by Rudra Brahm on 2011-06-01
Hi everyone, is there a way to find out BIOS password from Ubuntu? I know how to reset/clear the password but all I want is to find out the password. Is it possible from Ubuntu? Please help me!

---

### Post by seawolf167 on 2011-06-01
Sorry no. BIOS passwords are usually set by system administrators so people cannot change BIOS settings or to lock out booting off other media.

If this is your personal computer, you can clear the BIOS password by setting the BIOS Clear jumper to recovery/pswd mode or removing the CMOS battery.

---

### Post by Rudra Brahm on 2011-06-01
Yes its my pesonal computer. I can clear the CMOS but the thing is I have the same password set with my second computer (sony vaio laptop) so the real problem is with my laptop because I have to go a lengthy process to recover the password. So what i am thinking is if I can find out the password for this computer that i am currently using (a desktop), then my problem is solved.

---

### Post by seawolf167 on 2011-06-01
You can reset your Ubuntu password following [these steps]("http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/").

As said previously, you cannot recover or find your BIOS password - you'll need to physically reset it.

---

### Post by I'mGeorge on 2011-06-01
> **Rudra Brahm said:**
> Hi everyone, is there a way to find out BIOS password from Ubuntu? I know how to reset/clear the password but all I want is to find out the password. Is it possible from Ubuntu? Please help me!

I don't think is possible to find a BIOS password from any OS in general.

---

### Post by Rudra Brahm on 2011-06-01
> I don't think is possible to find a BIOS password from any OS in general.

I have done some google search and I found out that there are some way out from DOS/Windows. So I thought there must be a way out from ubuntu too. Anyway thanks everyone for your response and help.

---

### Post by binkles on 2011-06-01
hirens

---

### Post by linuxinstalledfromhdd on 2011-06-01
Pull the BIOS jumper with the unit unplugged.   If it is a desktop unit, unhook the power supply to the board.  Try to locate the original manual for the motherboard online. Research the correct way to reset the BIOS.  Then pull the jumper to reset. No more BIOS password. If it is a laptop, take it to a professional.

---

### Post by Habitual on 2011-06-01
> **I'mGeorge said:**
> I don't think is possible to find a BIOS password from any OS in general.

I'd have to agree.

In 17 years, I have only seen 1 BIOS password "cracked".

---

### Post by I'mGeorge on 2011-06-01
> **Rudra Brahm said:**
> I have done some google search and I found out that there are some way out from DOS/Windows. So I thought there must be a way out from ubuntu too. Anyway thanks everyone for your response and help.

I don't know where you've found that but as far as I know what can be done from Linux or windows alike is to override BIOS so the new installed BIOS won't be needing a password. Of course that's a risky thing to do as you have to know very well the motherboard's characteristics and usually flashing BIOS from inside an operating system implies a lot of risks.

A failed BIOS upgrades means you need a new BIOS chip

---

### Post by Allavona on 2011-06-02
Manufacturers sometimes have a "master" password that will let you into bios to reset the password.

It's a Sony so it's probably phoenix bios. Try simply "phoenix" at the password prompt screen.

If that doesn't do it you'll have to go rounds with Sony Tech Support. They do it by using serial number to generate the master pass for your model, but you'll have to provide them a ton of information.

---

### Post by Rudra Brahm on 2011-06-02
Yes I am aware of the risk. Anyway I will clear the password for my desktop with the jumper/battery method, and for my laptop I will talk to the sony servicing centre. Thanks everyone :)

---

