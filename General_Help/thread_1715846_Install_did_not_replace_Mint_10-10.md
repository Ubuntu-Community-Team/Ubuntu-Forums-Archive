---
title: "Install did not replace Mint 10-10"
date: 2011-03-27
forum: General Help
---

### Post by jagwinn on 2011-03-27
Hello,
I have Mint 10-10 and XP dual and nothing wrong here, works as planned.
I have been using Ubuntu 10 for a week on another HD and decided to replace Mint with Ubuntu.

I installed from DVD and it looked okay during install....said it was successfull and please restart computer. I did. And my usual screen came up with either Mint or XP but no Ubuntu.

Any ideas...on how to uninstall Mint10 (I'm worried about GRUB if I do) or why didn't Ubuntu replace MInt?

Thanks,
John

---

### Post by kolmad on 2011-03-27
Go to system>administation>synaptic package manager then search the pakage u want to remove/install

---

### Post by coffeecat on 2011-03-27
Since you are still getting the Mint grub menu for Mint and Windows, then the Ubuntu installer clearly didn't replace Mint with Ubuntu on the same partition. If the Ubuntu installer seemed to do an installation then it must have created another partition or used another partition for Ubuntu. But in that case I would have expected it to have installed Ubuntu's grub to the mbr and for you to get an Ubuntu grub menu with Ubuntu, Mint and Windows as choices. So something odd has happened.

In order to decide what to do next, you need to know what is on your system. It would be useful to run the boot info script here. This is usually used for diagnosing boot problems, but it will provide all the information we need to see what is going on. Boot into either Mint or the Ubuntu live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the script and post the RESULTS.txt file in code tags as described there. I'm logging off soon, but I will look at this thread in the morning (local time) and help if I can.

By the way, the previous poster mentions Synaptic which is used for installing or uninstalling packages. I have no idea why they should suggest this for this problem.

---

### Post by jagwinn on 2011-03-28
Hello Coffeecat and other gracious replies,

The install of these OS's was just that day, and having really nothing to lose, I formated the HDD and then installed WinXP then allowed Ubuntu to install itself, accepting all defaults.

It now works beautifully and I'm happy with it!

I retain WinXP until I can get AutoCAD, FamilyTreeMaker and ChurchTrac to work with Ubuntu.

I notice you are from the UK, on Saturday, a pharmaceutical facility [Catalent] suffered a fire..it was a packager for some of our [GlaxoSmithKline] products and now we will be adding work here to supply the EU with Nicorette [Commit] Nicotine Lozenges.

Thanks again for all the help, I feel welcome here,
John
Aiken, SC USA

---

### Post by coffeecat on 2011-03-28
> **jagwinn said:**
> I retain WinXP until I can get AutoCAD, FamilyTreeMaker and ChurchTrac to work with Ubuntu.

Good luck with that. If you mean getting them to work in wine in Ubuntu then that can be a bit hit or miss.

There's a good genealogy app for Linux called gramps. It's in the Ubuntu repository. It worked fine for my needs when I was doing some genealogy research. It can import and export various formats so you might be able to import your data created in FamilyTreeMaker. It probably isn't as glitzy-looking as some commercial software but it does the job well. Worth a try.

---

### Post by jagwinn on 2011-03-28
I will try GRAMPS. Don't need fancy, just a way to keep track!
Thanks,
John

---

