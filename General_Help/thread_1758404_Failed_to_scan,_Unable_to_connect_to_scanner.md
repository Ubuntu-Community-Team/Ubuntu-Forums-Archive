---
title: "Failed to scan, Unable to connect to scanner"
date: 2011-05-14
forum: General Help
---

### Post by BbUiDgZ on 2011-05-14
Ok, so a few weeks back my 6 year old daughter wanted to scan a picture she had made for a school project, I hadn't used my AGFA snapscan e20 for years, Infact it had been in a box for more than 5 years.

anyhoo I thought I'd give it a go and with some doubt plugged it in. Much to my joy and my daughters joy it just worked, there was life in the old dog still :D

So two or three weeks on after I've installed a kernel update as well as others on my daughters Dell Optiplex GX620 Ubuntu 10.04 LTS (2.6.32-30-generic #59-Ubuntu SMP), my multi operating system literate 6 year old has drawn another master piece and popped it in the scanner only to recive the following error from simple-scan
[quote="simple-scan"]
Failed to scan, Unable to connect to scanner
[/quote]
I open the simple-scan properties and I can see my scanner, so I run
```
tail -f /var/log/*
```
and retry the scan... nothing from my tail output.

What I'd like to know is,
1, How do I remove the entry for the scanner in simple-scan (ahh the old reinstall never fails)
2, why am I getting nothing back from my tail

3,Why did it break in the first place?

4, how to fix it (if not with a reinstall)

Please help as I don't want to break the "My Dad can fix anything" illusion my daughter has just yet.

Thanks,

---

### Post by Hedgehog1 on 2011-05-14
> **BbUiDgZ said:**
> Please help as I don't want to break the "My Dad can fix anything" illusion my daughter has just yet.

I think the quickest solution is to use the Ubuntu Software Center, and un-install both xsane and simple scan, and then reinstall them again using the Software Center.

Your daughter should not notice if you are quick...


The Hedge

:KS

---

### Post by BbUiDgZ on 2011-05-15
> **Hedgehog1 said:**
> I think the quickest solution is to use the Ubuntu Software Center, and un-install both xsane and simple scan, and then reinstall them again using the Software Center.

Your daughter should not notice if you are quick...


The Hedge

:KS

Didn't work :(

---

### Post by dragonfly41 on 2011-05-15
Shown as supported here ..

[http://www.sane-project.org/sane-mfgs.html#Z-AGFA](http://www.sane-project.org/sane-mfgs.html#Z-AGFA)

---

### Post by Irony on 2011-05-15
You need to delete your hidden config folder in your home directory, i.e. delete anything that looks like;

```
~/.xsane
```

---

### Post by BbUiDgZ on 2011-05-15
> **Irony said:**
> You need to delete your hidden config folder in your home directory, i.e. delete anything that looks like;

```
~/.xsane
```

thanks, 

its actually a common fault, I just didn't think I had the firmware problem due to the fact it worked the first time. I just booted windows xp on my other partition which loaded the firmware into the scanner then booted back into Ubuntu - it'll be fine as long as I don't power the scanner off.

The reason it worked the first time is because windows had already loaded the firmware

---

### Post by dino99 on 2011-05-15
is ubuntu installed via wubi ? if so, make a real install to stop headaches

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by tredegar on 2011-05-15
> The reason it worked the first time is because windows had already loaded the firmware

Looks like you need the file **snape20.bin** which should be somewhere on your windows disk, copied over to your linux partition, then an edit of **snapscan.conf**

See [here]("http://www.flagar.com/en/risorse/linux_inspiron_mandrake8.1") (scroll down to **Scanner AGFA Snapscan e20**)

---

### Post by barkhat on 2011-06-22
I am having this problem, too. Using Natty, I have a Iriscan Express 2 portable scanner. Ubuntu recognizes the scanner just fine and scanner is working (having tried it on my Windows 7 program a few minutes earlier. But I desire to withdraw from Windows completely). However, when I click 'scan' in the SimpleScan software, I get "Failed to scan, Unable to connect to scanner." Being still quite a novice I am not sure where to begin to figure out how to make it work. My Google search led me here.

I'd appreciate all advice to get this thing going. Thank you.:confused:

---

