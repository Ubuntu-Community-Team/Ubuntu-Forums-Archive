---
title: "Why No Option for 11.04 in Update manager"
date: 2011-07-03
forum: General Help
---

### Post by sunasia on 2011-07-03
Why doesnt my Ubuntu 10.04 have the option in the update manager to update to 11.04, Whereas I have a colleague with  the same OS and his has the option to do so?

---

### Post by plucky on 2011-07-03
> **sunasia said:**
> Why doesnt my Ubuntu 10.04 have the option in the update manager to update to 11.04, Whereas I have a colleague with  the same OS and his has the option to do so?

Because 10.04 is a Long Term Support (LTS) release.

Open Software Sources and under the Update Tab,change the Release Upgrade from LTS to Normal Releases.Reload and see if it now offers you the upgrade to 10.10.


And anyhow you would have to upgrade to 10.10 and then to 11.04.Probably easier to do a clean install of 11.04.

Good Luck

---

### Post by sunasia on 2011-07-03
ok thanks it does offer update to 10.10 , do i lose any data in my documents if I install to 10.10?

---

### Post by nzjethro on 2011-07-03
> **sunasia said:**
> ok thanks it does offer update to 10.10 , do i lose any data in my documents if I install to 10.10?

No, you shouldn't lose any data. The update manager will only affect system files. However, I read about upgrades gone wrong on these forums too often for me not to give the advice to **have a tested back-up of anything you wouldn't want to lose.**

Another question is, why are you upgrading from 10.04 to 10.10. 10.04 as a Long Term Support release, and is supported though to April 2013, whil 10.10 is a regular rolling release, and thusgoes EOL in April 2012. Is there any specific way reason you are wanting to upgrade from 10.04 to 10.10?

---

### Post by sunasia on 2011-07-03
Thanks for info, Actually the main reason is to try and get the sound sorted on this new notebook, I cant use the Microphone, I have been trying everything , I  had advice from others on forums and ideas about how to get it sorted, but this Pulse audio and alsa sound is unresponsive whatever i try. One poster said  they had problems with sound and updated to 11.04 and sorted so Maybe thats the way , What do you think? Is it a simple process to do these updates

---

### Post by Wim Sturkenboom on 2011-07-03
> **sunasia said:**
> ok thanks it does offer update to 10.10 , do i lose any data in my documents if I install to 10.10?

**[COLOR="Red"]Make backups[/COLOR]** if the data is important to you; upgrades can go wrong and you can loose data.

---

### Post by nzjethro on 2011-07-04
> **sunasia said:**
> One poster said  they had problems with sound and updated to 11.04 and sorted so Maybe thats the way , What do you think? Is it a simple process to do these updates

I've heard of similar problems with audio being resolved by updating to 11.04. If you download the 11.04 .iso, you can run "Live", without replacing 10.04. This will show you if 11.04 will be compatible with your audio hardware. As a piece of advice, when you create your Live CD, make it "persistent", so that any changes you make to the 11.04 system will be kept (this may only be an option with a Live USB). I would also recommend using the 11.04 Live CD for a week or so to see whether it is to your liking before upgrading/installing, as it is not everyone's cup of tea. But if you like it, I'd say go for it. :D

Did you post a thread here dealing with your audio issues?

---

### Post by dcstar on 2011-07-05
> **sunasia said:**
> ok thanks it does offer update to 10.10 , do i lose any data in my documents if I install to 10.10?

You should have a separate /home partition and then you can install/reinstall Ubuntu releases as many times as you like without loss of user data - do a forum search for detailed instructions.

"Updating" from one version to another invariably results in a setup less stable than a clean install - experienced Ubuntu users avoid updating and/or installing new versions until at least 2 months after official release.

---

