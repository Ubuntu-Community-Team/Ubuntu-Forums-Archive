---
title: "failed to install Virtuallbox 4.0.4"
date: 2011-03-12
forum: General Help
---

### Post by snake_eyes on 2011-03-12
Hello,

I'm trying to install the VirtuallBox 4.0 build 4 but I'm getting the following error message:

```
(Reading database ... 327010 files and directories currently installed.)
Unpacking virtualbox-4.0 (from virtualbox-4.0_4.0.4-70112~Ubuntu~karmic_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing virtualbox-4.0_4.0.4-70112~Ubuntu~karmic_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/virtualbox-4.0/VirtualBox.chm')
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
```

I ran sudo apt-get remove virtuallbox-4.0 in order to remove the old build

Please note that I restarted the computer but still I'm getting the same error, any help please?

Sincerely,

---

### Post by Hedgehog1 on 2011-03-12
I installed my vbox 4.0.4 by downloading the file called:

**virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_amd64.deb**

into my download folder, then right clicked on the file and chose:

**Open with Ubuntu Software Center** 

The software center came up, and I pressed the [Install] button.

***The Hedge***

:KS

---

### Post by snake_eyes on 2011-03-12
> **Hedgehog1 said:**
> I installed my vbox 4.0.4 by downloading the file called:

**virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_amd64.deb**

into my download folder, then right clicked on the file and chose:

**Open with Ubuntu Software Center** 

The software center came up, and I pressed the [Install] button.

***The Hedge***

:KS

I right clicked on the file but there is no 
**Open with Ubuntu Software Center** how I can add it?

---

### Post by Hedgehog1 on 2011-03-12
Right click on the: 

**virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_amd64.deb**

Select '**Open With Other Application**'

Select '**Ubuntu Software Center**'

***The Hedge***

:KS

---

### Post by snake_eyes on 2011-03-12
> **Hedgehog1 said:**
> Right click on the: 

**virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_amd64.deb**

Select '**Open With Other Application**'

Select '**Ubuntu Software Center**'

***The Hedge***

:KS

No **Ubuntu Software Center** in the list, I selected Custom commend and I wrote /usr/bin/software-center it open the Ubuntu Software without the virtuallbox

```
Linux delta 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux
```

---

### Post by Hedgehog1 on 2011-03-12
OK then.

In the terminal:

```

/usr/bin/software-center '/home/**[COLOR="Red"]hedgehog[/COLOR]**/Downloads/virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_amd64.deb'
```

Replace **[COLOR="Red"]hedgehog[/COLOR]** with your user name.

***The Hedge***

:KS

---

### Post by Old_Grey_Wolf on 2011-03-12
It looks like you are trying to install the Karmic (9.10) version of Virtualbox on Lucid (10.04). If so, download the Lucid version of Virtualbox and be sure to select i386 if you're running 32-bit Ubuntu.

---

### Post by snake_eyes on 2011-03-12
> **Old_Gray_Wolf said:**
> It looks like you are trying to install the Karmic (9.10) version of Virtualbox on Lucid (10.04). If so, download the Lucid version of Virtualbox and be sure to select i386 if you're running 32-bit Ubuntu.

Oh ****, I didn't notice that :) but I'm not sure why I selected the karmic, but what I remember it is I copied the link from the popup message that appear when a new release appear in the virtualbox, so maybe there was wrong with the link from scratch :), yuupiiiiiii it works as well :D

Thank you Old_Gray_Wolf really appreciated!

Yours Sincerely,

---

### Post by Hedgehog1 on 2011-03-13
> **Old_Gray_Wolf said:**
> It looks like you are trying to install the Karmic (9.10) version of Virtualbox on Lucid (10.04). If so, download the Lucid version of Virtualbox and be sure to select i386 if you're running 32-bit Ubuntu.

I missed that too!

The more sets of eyes, the better.

***The (near sighted) Hedge***

:KS

---

### Post by Old_Grey_Wolf on 2011-03-13
> **Hedgehog1 said:**
> I missed that too!

The more sets of eyes, the better.

***The (near sighted) Hedge***

:KS

I almost overlooked it myself. I can't blame my cataracts anymore now that I had the surgery to remove them. :)

I was staring at this line in post number 5
```
Linux delta **2.6.32-29**-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 **i686** GNU/Linux
```
trying to figure out why the OP posted what looked like the output from "uname -a".

Then it hit me. It doesn't matter why he posted it. It told me the answer. It said Lucid 32-bit, see the bold font I emphasized in the line.

:lolflag:

[sarcasm]Of course everyone knows the current Kernel number for every GNU/Linux Distro in use these days.[/sarcasm] :)

I was watching when a Red Hat Enterprise Linux 5.4 machine booted at work last Friday, and noticed it was Kernel 2.6.18. I was thinking, wow, that's old. :)

---

