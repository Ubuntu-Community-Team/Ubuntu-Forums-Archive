---
title: "How to type Korean in Ubuntu 10.04"
date: 2010-05-31
forum: General Help
---

### Post by razorboy5 on 2010-05-31
Hey 
How do u add languages in 10.04?
I went to System -> Pref -> Keyboard and added Korean and nothing happened for me

found a few instructions but were way too dated
would be grateful for any tips :P

---

### Post by Exp HP on 2010-05-31
That changed nothing for me either.  So I found where it allows you to get the input methods.

Did you go to Language Support (under System>>Administration in the panel) and install the Input Methods for Korean (click Install / Remove Languages...)?  I'm currently doing that to see if that will allow me to select one of the modes mentioned on this page:
[http://www.jw-stumpel.nl/stestu.html#T6.6.2](http://www.jw-stumpel.nl/stestu.html#T6.6.2)

---

### Post by Exp HP on 2010-05-31
Unless I'm mistaken, the thing I suggested before added the "nabi" input method to the menu in Language Support after a logging out and back in.  Unfortunately, many users of Ubuntu have reported nabi as no longer working in 10.4.

However... I got the SCIM input method working.

First and foremost, in Keyboard Layouts, I added the Korean keyboard layouts and removed the US one, and applied system wide.  I don't know if this made any significant difference or not, but at least that stopped it from switching back to USA when I logged out.

Anyways,
Install the scim-hangul package:
```
sudo apt-get install scim-hangul
```Log out and back in.
In Language Support, select "scim-bridge" for Keyboard input method system.

From here, don't even bother doing anything else, and just **restart the computer**.  I don't know what I did, but I got stuck for a while with what seemed to be a dysfunctional spell checker for English assigned to the Hangul (right alt) key, and I couldn't figure out why it was there.  Just restart.

And voila.  Now you can switch to Hangul mode by pressing Right Alt or Ctrl+Space.
&#47924; &#12596;&#54728;&#12624;&#54676; &#54784;&#45852;&#47726; 
(for anyone wondering, that's just random letters)

---

### Post by razorboy5 on 2010-05-31
&#44048;&#49324;&#54632;&#45768;&#45796;~ &#12622;&#12622;
works like a charm :) right alt doesn't change languages for me but ctrl+space does, a lil bothersome but no big whup 

thx again :)

---

### Post by Exp HP on 2010-05-31
Glad I could be of help!

Oh, and it turns out the Right Alt thing depends on whether or not you are using the **Korea, Republic of** or **Korea, Republic of 101/104 key Compatible** layout.  The standard one lets you use Ctrl and Alt normally, while the 101/104 key one replaces Right Alt key with Hangul and the Right Ctrl key with Hangul Hanja (which brings up a list of characters to select from).

---

### Post by paker on 2010-06-12
> **Exp HP said:**
> ........ in Keyboard Layouts, I added the Korean keyboard layouts and removed the US one, and applied system wide.  Do you mean the machine boots up in Korean? And add English keybopard afterward? Thanks in advance for clarification.

I am still using 9.10 because of Korean input issues with 10.04.

---

### Post by simosx on 2010-06-14
I think that since Ubuntu 10.04 switch from SCIM to IBus, the proper solution would be to use IBus instead of SCIM.
If IBus cannot do something that SCIM used to do, then this is a bug in IBus and should be reported/fixed.

If we do not do this job,then problems will appear again and again in each version of Ubuntu.

---

