---
title: "Localized version of Thunderbird"
date: 2010-03-08
forum: General Help
---

### Post by HiSiskin on 2010-03-08
Ubuntu official package of the Mozilla Thunderbird, which I think is much better than Evolution as a mail client particularly in its UI usability, is old in version and English only.

If you want to have a localized vesion in different languages, e.g. I am a Japanese, you should go to Mozilla official site to get a tar.bz2 file for Linux.

My question is: an application installed that way  becomes an outsider, or a stranger, to the Ubuntu eco-system on user's local system environment. Could we convert it to a legitimate insider, i.e. putting it under the Ubuntu proper package management scheme, via a relatively simple way? If yes, how?

---

### Post by artheus on 2010-03-08
> **HiSiskin said:**
> Ubuntu official package of the Mozilla Thunderbird, which I think is much better than Evolution as a mail client particularly in its UI usability, is old in version and English only.

If you want to have a localized vesion in different languages, e.g. I am a Japanese, you should go to Mozilla official site to get a tar.bz2 file for Linux.

My question is: an application installed that way  becomes an outsider, or a stranger, to the Ubuntu eco-system on user's local system environment. Could we convert it to a legitimate insider, i.e. putting it under the Ubuntu proper package management scheme, via a relatively simple way? If yes, how?

What do you mean with "converting it to a legitimate insider"?

Do you mean you want to be able to run it only by the command "thunderbird" and creating launchers? Or du you mean something even more advanced than that?

//Artheus

---

### Post by Pjotr123 on 2010-03-08
There is a bug in language support: when you install Thunderbird from the repo's in a non-English-Ubuntu, it's still English-only. Reason: the localized language packs from Thunderbird aren't installed automatically....

Solution: run System - Administration - Language Support. The missing localized language packs are then offered automatically (you only have to click "OK").

Of course this shouldn't be necessary. I'm considering filing a bug report on Launchpad.

--Edit--

I've filed a bug report on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/534417](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/534417)

Feel free to support it there! :-)

---

### Post by HiSiskin on 2010-03-08
&gt; Solution: run System - Administration - Language Support.
Thanks for the valuable answer. I also have learned the term 'Germania Secunda' from Wikipedia!

> **Pjotr123 said:**
> There is a bug in language support: when you install Thunderbird from the repo's in a non-English-Ubuntu, it's still English-only. Reason: the localized language packs from Thunderbird aren't installed automatically....

Solution: run System - Administration - Language Support. The missing localized language packs are then offered automatically (you only have to click "OK").

Of course this shouldn't be necessary. I'm considering filing a bug report on Launchpad.

--Edit--

I've filed a bug report on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/534417](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/534417)

Feel free to support it there! :-)

---

