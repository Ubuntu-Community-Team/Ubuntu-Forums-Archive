---
title: "Software center questions (Ubuntu 11.10)"
date: 2011-10-17
forum: General Help
---

### Post by Lólindir on 2011-10-17
Dear all,

I have some questions regarding how the software center is working in Ubuntu 11.10, cause it's not working transparent, or at least not completely as I would expect.

To give some examples:

[LIST]
[*]I wanted to install *adobe flash*.
I went to the software center, I typed in the search box '*adobe flash*', and I get 2 versions of adobe flash: *Adobe Flash plugin* (which seems to be version 11) and *Adobe Flash plugin 10* (which seems to be version 10 of the adobe flash player).
I then installed adobe flash via command line (apt-get install adobe-flashplugin) and came back to the software center. I expected that one of the 2 options would now be marked as 'installed', but this was not the case. Both options appeared as '*not installed*', however if I open firefox, the adobe flash plugin is active.
Is this behavior normal?

[*]When you are looking something up in the software center, you are by default looking among '*All Software*'. You can also choose for '*Provided by Ubuntu*', '*Canonical Partners*', '*For Purchase*', and in my case also '*Oracle Corporation*, since I've installed VirtualBox via the Oracle repository.
When I look up '*adobe flash*' in '*All Software*' I get 2 results. I would expect to find those 2 results back in one of the above subcategories, but this is not the case: I can find back '*Adobe Flash plugin 10*' in the category '*Canonical Partners*', but I can not find back the *Adobe Flash plugin (version 11)* in one of the subcategories. Is this a bug or am I doing something wrong?

[*]I've added the Orcale Virtual Box repository to my Ubuntu, and I looked up VirtualBox in the software center.
When I do a normal lookup in the '*All Software*' category I get one result: the by Ubuntu provided VirtualBox 4.1.2.
When I then choose the subcategory '*Oracle Corporation*', I see the by Oracle provided Virtualbox 4.1.4.
Why is this last version not showing up in the '*All Software*' category?
[/LIST]

Maybe I misunderstand the concept and working of the software center, but it doesn't seem to be (completely) transparent to me. I think it's a good concept, and it can be a good user-friendly tool, but the issues mentioned above makes it feel as a big black box which is not behaving as I expect, which makes me a bit scared to use it.
Or maybe I am using the software center wrongly?

Best regards,

Lólindir

---

### Post by lovinglinux on 2011-10-17
1 - The *adobe-flashplugin* is marked as version 10 in Software Center, but is actually version 11.0.1.152. You can see that in the details. The package *flashplugin-installer* is also version 11.0.1.152, but I suspect if you are using  64bit system, it still installs the 32bit wrapper, while *adobe-flashplugin* installs the real 64bit plugin. I juts did a test, installing one then the other and they are respectively marked on Software Center as installed. So, it is probably a bug on your system.

2 - I suspect the filter doesn't include applications from universe and multiverse, which are no maintained by Canonical or partners. So, you need to use All Sofware to find those.

3 - I suspect another bug. I did a search for System Monitor Indicator, which is installed via ppa and it didn't show up in the All Software list. However, when I search for the package name *indicator-sysmonitor* it shows up. So is probably an issue related to searching for the application title.

---

### Post by Lólindir on 2011-10-17
Hi,

Thanks for the quick reply!

1 - You are correct regarding the version numbers. adobe-flashplugin is indeed pointing to Adobe Flash Plugin 10 (which is actually version 11). Strange that when I install adobe-flashplugin via the command line, it doesn't show up as installed in the software center. Seems to be a bug. Can I post this bug somewhere?

2 - Still seems to bit a bit strange behavior to me...

3 - If I look up the package name I indeed also get the result in All Software. Seems to be a bug as well (or at least a missing feature).

---

### Post by lovinglinux on 2011-10-17
> **Lólindir said:**
> Hi,

Thanks for the quick reply!

1 - You are correct regarding the version numbers. adobe-flashplugin is indeed pointing to Adobe Flash Plugin 10 (which is actually version 11). Strange that when I install adobe-flashplugin via the command line, it doesn't show up as installed in the software center. Seems to be a bug. Can I post this bug somewhere?

2 - Still seems to bit a bit strange behavior to me...

3 - If I look up the package name I indeed also get the result in All Software. Seems to be a bug as well (or at least a missing feature).

Please report the bug on [launchpad](https://bugs.launchpad.net/ubuntu/)

---

### Post by Lólindir on 2011-10-18
Bugs submitted:
[https://bugs.launchpad.net/bugs/877302](https://bugs.launchpad.net/bugs/877302)
[https://bugs.launchpad.net/bugs/877319](https://bugs.launchpad.net/bugs/877319)

---

### Post by lovinglinux on 2011-10-18
> **Lólindir said:**
> Bugs submitted:
[https://bugs.launchpad.net/bugs/877302](https://bugs.launchpad.net/bugs/877302)
[https://bugs.launchpad.net/bugs/877319](https://bugs.launchpad.net/bugs/877319)

Thanks.

---

### Post by giggolo on 2011-10-22
Anyone out there has the software center open up blank. I also can't close the software center after it opens "blank"

---

### Post by babanesma on 2011-10-23
> **giggolo said:**
> Anyone out there has the software center open up blank. I also can't close the software center after it opens "blank"

I have the same problem

---

### Post by egkeat on 2011-10-23
My software center now opens up without a way to search software.

---

### Post by pushpsmarty on 2011-10-29
when i try to install adobe flash plugin 10 then software center giving me message that it's not present in software center instead of displaying "Use this source".
So mean is that not coming the option of cache updating.
How  can i do it manually by terminal.
There are two screenshots given.

---

### Post by pushpsmarty on 2011-10-29
> **pushpsmarty said:**
> when i try to install adobe flash plugin 10 then software center giving me message that it's not present in software center instead of displaying "Use this source".
So mean is that not coming the option of cache updating.
How  can i do it manually by terminal.
There are two screenshots given.
It's very funny i got this error and there is a solution which you can try if this error is encountered.
run this command on terminal-
sudo apt-get update
and then re-open software center hope this would work now.

---

### Post by oldtimer7777 on 2011-10-29
> **pushpsmarty said:**
> It's very funny i got this error and there is a solution which you can try if this error is encountered.
run this command on terminal-
sudo apt-get update
and then re-open software center hope this would work now.

Software Center is much slower than Synaptic Package Manager:

sudo apt-get install synaptic
sudo synaptic

Way more flexible. Way more customizable and faster.

---

