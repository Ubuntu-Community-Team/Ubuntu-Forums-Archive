---
title: "Thunderbird messages don't display correctly"
date: 2010-08-28
forum: General Help
---

### Post by malkdude on 2010-08-28
Hi ubuntuers. I am having problems with Thunderbird in Ubuntu Lucid. I am not sure since when. It could have been since I upgraded to Lucid from Karmic. When I open Thunderbird, a message pops up that is supposed to ask me for the password. However, it is all blank inside and doesn't display the text. I found that after I click on ALT+TAB a few times, the message displays correctly. This is very strange. Is anyone else having (or had) the same problem? Does anyone have an idea for a fix?

I tried uninstalling and then reinstalling but it didn't work out (I didn't "purge" though). :confused:

---

### Post by malkdude on 2010-08-28
I would like to add that upon deactivating compiz and setting effects to none, Thunderbird behaved normally. Thus this is some kind of conflict between thunderbird and compiz. It has been reported in

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/564011](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/564011)

The "fix" mentionned there was to install thunderbird from somewhere else...

---

### Post by malkdude on 2010-08-29
Downloading the latest Thunderbird from the Mozilla website itself fixed it!

---

### Post by MisterLambda on 2010-08-29
FYI, SeaMonkey builds are also broken (Mail is dysfunctional and suite randomly crashes) and Firefox is built with some of the slowest build options available.

I cannot stress this enough: **download Mozilla apps from the offical site!** This fixed my SeaMonkey crashing and problems.

I have no idea why the packages are shipping such defective builds.

---

### Post by malkdude on 2010-08-29
thanks for the info MisterLambda.

---

