---
title: "Ubuntu secretly changes my browser language setup without my request"
date: 2011-08-07
forum: General Help
---

### Post by Jerriy on 2011-08-07
I had that standard "Ubuntu Firefox Modifications" addon/extension in my browser and it turned out that one of the things it does is automatically manipulate the language settings in Firefox so that it reverts to a setting everytime firefox starts. So basically in my Ubuntu computer I am not allowed to change the preset of the language of my browser.   

This is the item controlled by the "intl.accept_languages" line in about:config, which everytime it is changed (either by me or by a software) Ubuntu sneaks up and reverts the setting back, so that every time I restart/reopen Firefox I am back to square one. The thing is this wasn't the case until recently. I have no idea what happened or when or how but obviously I don't want it and I want to know how I can get back to the way it was.

---

### Post by Jerriy on 2011-08-07
This is a recent and very worrying development for two reasons: 1) it hampers me practically as I need to be able to manually change that myself for my work on the computer (related to security software among other things), and (2) the very idea that Ubuntu takes over and takes away control of a setting AWAY from me is a rather worrying development since that resembles a new way of dealing with issues rather than the traditional open source way of doing things (letting the user have the choice to do one thing or another). I didn't switch to Ubuntu so that Ubuntu becomes another Microsoft clone.

---

### Post by Jerriy on 2011-08-07
Needless to say I have disabled the Ubuntu extension/addon/plugin in my browser until this is solved.

---

### Post by mikewhatever on 2011-08-07
Do you always tend to fall for conspiracy theories, or just this time?

Edit: "init.accept_language" doesn't exist here, and Google turns up nothing as well. To make yourself feel better, you can remove the 'ubufox' and 'xul-ext-ubufox' packages and restart the browser.
Make sure there is no black van under your window first. ;)

---

### Post by Jerriy on 2011-08-07
> **mikewhatever said:**
> Do you always tend to fall for conspiracy theories, or just this time?

Edit: "init.accept_language" doesn't exist here, and Google turns up nothing as well.Sorry, that's a spelling mistake in my OP. It's **intl.accept_languages**

---

### Post by westie457 on 2011-08-07
> **Jerriy said:**
> I had that standard "Ubuntu Firefox Modifications" addon/extension in my browser and it turned out that one of the things it does is automatically manipulate the language settings in Firefox and reset it so that everytime firefox starts. I found out that basically in my Ubuntu computer I am not allowed to change the preset of the language of my browser.   

This is the item controlled by the "init.accept_language" line in about:config, which everytime it is changed (either by me or by a software) Ubuntu sneaks up and reverts the setting back, so that every time I restart/reopen Firefox I am back to square one. The thing is this wasn't the case until recently. I have no idea what happened or when or how but obviously I don't want it and I want to know how I can get back to the way it was: letting ME in control of the language setting of MY computer.

Firstly open FF go to Edit, Preferences. In the Content tab Choose the language you want to use and remove all those you do not want. Close and restart ff to check things are okay. 

If not go to System, Administration, Language support and set your desired language the both of the available tabs. Log out and back in to check all is well.

If not then I have no other suggestions for you and apologise for wasting your time.

---

### Post by Jerriy on 2011-08-07
> **westie457 said:**
> Firstly open FF go to Edit, Preferences. In the Content tab Choose the language you want to use and remove all those you do not want. Close and restart ff to check things are okay. That is already the setup in my FF preferences so I guess we can conclude that that's not what's causing the issue.

> If not go to System, Administration, Language support and set your desired language the both of the available tabs.Is that what's affecting behaviour of the Ubuntu ff extension? Cuz I do have multiples of language support in my operating system administration (for use in not so much Firefox but more things like OpenOffice and spreadsheet and so forth). Anyway l'll tinker with that and let's see what happens.

---

### Post by lovinglinux on 2011-08-08
> **westie457 said:**
> Firstly open FF go to Edit, Preferences. In the Content tab Choose the language you want to use and remove all those you do not want. Close and restart ff to check things are okay...

> **Jerriy said:**
> That is already the setup in my FF preferences so I guess we can conclude that that's not what's causing the issue.

Is that what's affecting behaviour of the Ubuntu ff extension? Cuz I do have multiples of language support in my operating system administration (for use in not so much Firefox but more things like OpenOffice and spreadsheet and so forth). Anyway l'll tinker with that and let's see what happens.

Are you trying to change the language of the web pages or the language of Firefox interface?

The preferences changes suggested above by westie457 controls *intl.accept_languages*, so changing either one of those has the same result. They control what language you prefer if a web site is offered in more than one language. They do not control the language of the interface. 

To change Firefox interface language, you need to install the corresponding language package ( for example, the Portuguese package is *firefox-locale-pt*), then change the pref *general.useragent.locale* accordingly or use an extension like [Quick Locale  Switcher]("https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/").

---

