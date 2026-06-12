---
title: "Very strange glitch with bank login"
date: 2010-04-15
forum: General Help
---

### Post by shelbyvision on 2010-04-15
My bank just changed their online banking setup. I never had any trouble with the old setup. Now when I log in, it goes to the right page, but in less than a second, it switches to a page that looks like it is intended for the webmaster, for making basic changes. Once it goes to this page I cannot navigate out of it. The reason I'm posting this here is that it works fine on my wife's computer; both hers and mine have ubuntu 8.04, with all the latest updates installed. Our settings for firefox appear to be identical. Both computers are laptops, mine an hp/compaq, hers an IBM. Any ideas why my computer is behaving this way? I talked to the "expert" at the bank, and she was no help at all. :confused:

---

### Post by stinkeye on 2010-04-15
Have you tried deleting your cookies and cache?

---

### Post by mcduck on 2010-04-15
> **shelbyvision said:**
> My bank just changed their online banking setup. I never had any trouble with the old setup. Now when I log in, it goes to the right page, but in less than a second, it switches to a page that looks like it is intended for the webmaster, for making basic changes. Once it goes to this page I cannot navigate out of it. The reason I'm posting this here is that it works fine on my wife's computer; both hers and mine have ubuntu 8.04, with all the latest updates installed. Our settings for firefox appear to be identical. Both computers are laptops, mine an hp/compaq, hers an IBM. Any ideas why my computer is behaving this way? I talked to the "expert" at the bank, and she was no help at all. :confused:

If you get into a page intended for administering the site, then the bug is definitely at the bank's end, not on your computer (and I'd seriously consider switching to another bank if the bank I use made as bad security mistake as users being able to access such page...)

---

### Post by shelbyvision on 2010-04-15
> **stinkeye said:**
> Have you tried deleting your cookies and cache?

Yes I tried that, it had no effect.

---

### Post by shelbyvision on 2010-04-15
> **mcduck said:**
> If you get into a page intended for administering the site, then the bug is definitely at the bank's end, not on your computer (and I'd seriously consider switching to another bank if the bank I use made as bad security mistake as users being able to access such page...)

As I said, it only does it on my computer. The page does not allow me to actually make any changes. It's totally useless to me.

---

### Post by stinkeye on 2010-04-15
Try another browser and see if you get the same result.

---

### Post by elliotn on 2010-04-15
speak to ur bank.

---

### Post by mcduck on 2010-04-15
> **shelbyvision said:**
> As I said, it only does it on my computer. The page does not allow me to actually make any changes. It's totally useless to me.
Have you actually tried to use the bank site on your wife's computer, but logging into *your* account on the bank's site?

I can't imagine any sane reason how anything on your computer could cause the bank's site to redirect you to a web page you shouldn't go to (even if somehting on yur computer culd cause such thing, it would still mean that there's a serious bug on the bank's site). That really, really sounds like a problem on their end, even though it might not happen to everybody (so I bet it's related to user account, not the computer you sue to log in to that site).

---

### Post by shelbyvision on 2010-04-15
> **mcduck said:**
> Have you actually tried to use the bank site on your wife's computer, but logging into *your* account on the bank's site?


Yes, my wife's login and my login both work on her computer. Neither my wife's nor my login will work on my computer, although using her login produces an error message instead of going to that useless page. I used her computer with my login yesterday to transfer funds from one account to another. Worked fine.

---

### Post by shelbyvision on 2010-04-21
This is interesting. Apparently this problem has something to do with extra software (third-party, unapproved, etc) that's been installed on my laptop. I tried it on my old desktop computer, which also had a lot of the same software, and it had the same glitch. I wiped it clean and installed Ubuntu 8.04 from the CD, and now the bank site works fine. I wish there was some way to determine which software is causing the problem. I don't want to have to remove it all from my laptop.

---

