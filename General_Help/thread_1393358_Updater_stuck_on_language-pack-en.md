---
title: "Updater stuck on language-pack-en"
date: 2010-01-29
forum: General Help
---

### Post by hangfire on 2010-01-29
Running 8.0.4LTS.

I can't get rid of the Adept Notifier applet because Adept Updater cannot download language-pack-en 1:8.04+20100117. It always comes up with a Requested of "no change". If I do a Request Upgrade it changes to "BREAK (upgrade)", but when I hit Apply Updates, I get the following error:

> **Could not commit changes - Adept Notifier**
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

I can live without a new language-pack-en, but I would like to clear it from my Adept Notifier, so I can see when I really do need updates.

-HF

---

### Post by HousieMousie2 on 2010-01-29
You're not alone, hangfire... which means they are probably working on it.

EDIT:

I guess I could have mentioned that for the time being you can simply hover your mouse over the Adept Notifier icon and see if it lists more than one updated package available.

Also... checked LaunchPad...  it has been posted, along with the information that this issue will resolve itself when language-pack-en-base is updated, which is the dependency that is breaking the language-pack-en installation.

---

### Post by Butthead on 2010-01-29
I cleared my Adept Notifier from showing it needed upgrading by hitting the blue "arrow" symbol next to it, choosing the "Details" box that then shows up, and then choosing the "Remove" box that then shows up.

I sure hope I wasn't too hasty in my repairs? :eek:

---

### Post by Jack Durain on 2010-01-31
same happened to me, also wanted to get rid of the adept notification for the language-pack-en, but now seems things are really broken:

uninstalled the language-pack-en-base, because I wanted to reinstall afterwards..
both language-pack-en and language-pack-en-base happily told "not installed"
but when I tried to reinstall language-pack-en-base, it now tells "BREAK" too!
no matter what I try now, in what combination ever, it's impossible to reinstall again 

this is quite annoying, so please fix this bug, or advise how to get around..

Jack ](*,)

---

### Post by a_hippie on 2010-01-31
Thanks for the heads up.  I actually  killed the notifier since it was bugging me last week.  rather surprised that it's still not resolved this week.  Anyway, I guess I will deal with it for the time being.

Thanks again for the heads-up.

regards,

---

### Post by hangfire on 2010-02-01
> **HousieMousie2 said:**
> Also... checked LaunchPad...  it has been posted, along with the information that this issue will resolve itself when language-pack-en-base is updated, which is the dependency that is breaking the language-pack-en installation.

Good to know, I checked launchPad as well but I guess I was too early. Wasn't sure what package to complain about, Adept or language-pack-en or what.

Just added myself as a fellow sufferer on Bug #514329.

-HF

---

### Post by a_hippie on 2010-02-01
The rest of the package was in tonights security update once I logged onto the net.  Adept did it's magic mojo and all is well again.  

If you killed adept, the next time you boot, the new packages will show up and clear your back-log.

Thanks Ubuntu and forum people!   :)

regards,

---

### Post by hangfire on 2010-02-02
> **a_hippie said:**
> The rest of the package was in tonights security update once I logged onto the net.  Adept did it's magic mojo and all is well again.

Applied updates too, and all is well here.

Amazing that such breakage would slip through on an LTS release. I guess the Conanical folks are very busy with 10.4.

-HF

---

