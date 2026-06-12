---
title: "Apparently you can't change your password unless Evolution is installed"
date: 2010-01-05
forum: General Help
---

### Post by user1397 on 2010-01-05
So I removed evolution along with some other default apps (because I do not use them) and then randomly today I was thinking about changing my user password, so I went to System > Administration > Users and Groups, clicked 'Properties' on my account, and then clicked 'Change Password,'  only to find this error message in a popup window:

There was an error while trying to get the addressbook information
Evolution Data Server can't handle the protocol

Yup, I know I can change it using the command [FONT=monospace]"[/FONT]sudo passwd USER_NAME" but I am just wondering about the gui way of doing things...is it broken just because I don't have evolution installed?

EDIT: Solution: So I went into synaptic and installed package 'evolution-data-server' (because that was part of the error message so i figured why not try it) and voila it works now. I didn't need to install evolution itself.

---

### Post by RiceMonster on 2010-01-05
```
sudo passwd USER_NAME
```

---

### Post by cariboo on 2010-01-05
System-->Preferences-->About Me, is where changing your password is now done. Remember to log out and back in again to make the change take affect.

---

### Post by user1397 on 2010-01-05
> **RiceMonster said:**
> ```
sudo passwd USER_NAME
```Please read my edit above.

---

### Post by user1397 on 2010-01-05
> **cariboo907 said:**
> System-->Preferences-->About Me, is where changing your password is now done. Remember to log out and back in again to make the change take affect.That gives me the same popup.

---

### Post by dcstar on 2010-01-05
> **ubuntuman001 said:**
> **So I removed evolution** along with some other default apps (because I do not use them) and then randomly today I was thinking about changing my user password, so I went to System > Administration > Users and Groups, clicked 'Properties' on my account, and then clicked 'Change Password,'  only to find this error message in a popup window:

There was an error while trying to get the addressbook information
Evolution Data Server can't handle the protocol


Evolution is a part of the base Gnome system, put it back.

---

### Post by rakete on 2010-01-05
> Evolution is a part of the base Gnome system...

Yeah, one of the biggest Gnome Problems... Evolution is buggy, unstable and most of the time: not working...

I hate the "Evolution Assistent" or the "Evolution Calender" pops up, every time I klick on the Gnome Calender. That sucks (Laptop getting slow, Resources go away, time is wasted)

If someone could come up with a replacement for all those little functionalitys, that make evolution mandatory in Gnome, I think that would be highly appriciated in the Gnome-World... I only know Ex-Windows Geeks using and loving Evolution, but imho: they should go and use a SuSe Linux with KDE...

Here at my company most Linux Users use Thunderbird, even though we have an Exchange Server, for these main reasons: Evolution crashes, freezes, forgets to remind Events and in Conclusion feels like an unstable Beta-Program for years now (firstly tested by me with 7.04)... No good for every day office use at all.

---

### Post by Georgia boy on 2010-01-05
I had removed Evolution from my system also. You mean we're not supposed to do so that it affects other systems if removed? I tried Evolution but didn't like the way it operates so I went back to Thunderbird and removed Evolution through Synaptic Package Manager. We don't need to have it put back do we?

Tom

---

### Post by audiomick on 2010-01-05
Hallo.
I don't know what breaks if you remove evolution, but I have seen many posts to the effect that it is integral to Gnome. I would suggest putting it back.

@ rackete: Actually, I like evolution, I don't like Suse & KDE, and I am definitely not an Ex-Windows Geek.:)

---

### Post by user1397 on 2010-01-05
So I went into synaptic and installed package 'evolution-data-server' (because that was part of the error message so i figured why not try it) and voila it works now.  I didn't need to install evolution itself.

---

### Post by dcstar on 2010-01-06
> **rakete said:**
> Yeah, one of the biggest Gnome Problems... Evolution is buggy, unstable and most of the time: not working...
.........

Rubbish, I - and many others - have been using Evolution with little or no problems for years now.

My last "problem" with Evolution was finding a bug in the Calendar code where repeated appointment data from a previous version wasn't being processed correctly - I filed a bug report and it was fixed in the next version.

I do wonder if the loud minority that are always ready to complain about Evolution ever actually do anything to get their issues addressed, or is it just easier to whinge and moan?

---

