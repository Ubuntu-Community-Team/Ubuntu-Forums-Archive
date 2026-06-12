---
title: "Korean keyboard"
date: 2009-10-22
forum: General Help
---

### Post by Nerd King on 2009-10-22
Hi,

Just wondering if you can help me. I work in a very international environment with British, American, Dutch, Swedish, Danish, Finnish, Thai, Korean, Japanese, Australian, German, Chinese and just about every other nationality. This of course adds a challenge when setting up linux. My big pain in the bottom is Korean. I can't get it to let me type in Korean (btw I'm British and can't speak a word of Korean, but will at least know it when I see it, so please bear that in mind!).

Any ideas?

Cheers,

Ryan

---

### Post by jrrader on 2009-10-22
My wife is Korean and I sometimes type in Korean so maybe I can help you.  I don't really know what you've done so far so I'll start from the beginning.  I'm sure you've done some of this.

First step would be System > Administration > Language Support.  Click the box for "Use IME to enter complex languages" and then click on Install/Remove Languages.  Find Korean and give it a check.  All five component boxes should be checked.  Then press Apply.  Admin password will pop up and then download dialogue.   Log out and then log back in again. 

Now you should see a keyboard icon at the top of your panel.  Pressing ctrl+space should allow you to switch between your languages.  The keyboard icon will change into &#54620; when it gets to Korean.  Right click on it to get to setup or go System > Preferences > SCIM Input Method Setup if you want to change shortcuts.  On Windows computers that do not have the hangul key, shift+space is usually used to switch languages.  If they need to type in hanja (Chinese characters), by default that is done by pressing F9 after entering the characters in hangul.  On their keyboards in Korea they have a key for that (Korean keyboards have very small space bars because of the hangul and hanja keys).

This has worked fine on all the computers I have in my house that are running 32bit Ubuntu.  On the computer I'm using now, which has 64bit Ubuntu, it does not work in Firefox - so I'm using Opera right now.  If you're using 64 bit, install Opera as the default browser for their accounts.

---

### Post by Nerd King on 2009-10-22
Excellent, I'll give this a try and hopefully my Korean friends will be much happier (Korean layout is QWERTY at the mo which sucks). I'd not done the IME bit which is perhaps where I had failed. Fingers crossed it'll work :)

---

### Post by jrrader on 2009-10-22
Let me know how it works.

Also, most of my coworkers back in Korea always had both MSN and NateOn (Korean language messenger) running.  If you have a user account for your Korean coworkers, change the language to Korean for that account and you can use Wine to install NateOn for them - [http://nateonweb.nate.com/download/messenger/windows/4.0/download.php](http://nateonweb.nate.com/download/messenger/windows/4.0/download.php) - I have tested it and it works fine.  You can only do that if you have a user account where Korean is the default language or most text will appear as boxes and question marks.  Have a Korean handy to read the install boxes if you aren't familiar with Windows installers.  Middle button to move forward, (A) radial to accept terms.

---

### Post by Nerd King on 2009-10-22
I'll send my Korean friends this thread, my tests look good as I managed to type Korean on my machine, yay! Thank you loads, you're a lifesaver :)

---

### Post by mathewd on 2010-03-07
> **jrrader said:**
> Let me know how it works.

Also, most of my coworkers back in Korea always had both MSN and NateOn (Korean language messenger) running.  If you have a user account for your Korean coworkers, change the language to Korean for that account and you can use Wine to install NateOn for them - [http://nateonweb.nate.com/download/messenger/windows/4.0/download.php](http://nateonweb.nate.com/download/messenger/windows/4.0/download.php) - I have tested it and it works fine.  You can only do that if you have a user account where Korean is the default language or most text will appear as boxes and question marks.  Have a Korean handy to read the install boxes if you aren't familiar with Windows installers.  Middle button to move forward, (A) radial to accept terms.

Just thought I'd point out... Pidgin can handle both MSN *and* NateOn. The NateOn plugin can be downloaded from, among other places, here [https://launchpad.net/~ubuntu-ko/+archive/ppa](https://launchpad.net/~ubuntu-ko/+archive/ppa)
i use it, works great for me on 9.10 to keep in touch with my korean friends.

---

