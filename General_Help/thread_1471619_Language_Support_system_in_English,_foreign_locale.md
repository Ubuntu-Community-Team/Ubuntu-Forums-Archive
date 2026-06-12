---
title: "Language Support: system in English, foreign locale"
date: 2010-05-03
forum: General Help
---

### Post by cyprys on 2010-05-03
I only want spellchecking, calendar and currency to be typical for Poland (this is where I currently live), Ubuntu itself (interface, applications, manuals) should be in English - I don't understand Polish well enough.

In 9.10 I used to check Polish spellchecking (translations were checked for install automatically but you couldn't tell unless you chose another language and then Polish again) and uncheck the translations. It allowed for setting locale (calendar/currency) to Polish and also keep the spellchecking. Now it's buggy: I can do a fresh install of Ubuntu but can't set Polish spellchecking, calendar (it starts from Monday), currency (it's PLN/z&#322;) and keep the system itself in English. What I do wrong?

1. Fresh install
2. *System -> Administration -> Language Support*
3. *Language -> Install / Remove Languages*
4. Find Polish and select ONLY: **Spellchecking and writing aids**
5. Text -> Display numbers, dates and currency amounts in: **Polish**

Confirm, reboot and... Bump! I've got Polish translations in several places, e.g.:

[img]http://ubuntuforums.org/attachment.php?attachmentid=155359&stc=1&d=1272920114[/img]

If I upgrade any software, it is in Polish. Firefox (or Namoroka) locale changes to "pl,en" and its plug-ins are in Polish by default. Every time I run *Language Support* again Ubuntu says:
> The language support is not installed completely
Some translations or writing aids available for your chosen languages are not installed yet. Do you want to install them now?
(bunch-of-PL-translations-here)

After I uninstall Polish translations (and leave spellchecking and writing aids as it was) there's a problem with locale (Polish locale is removed along with translations), besides, system doesn't actually change back to English and newly installed applications either crash with errors or install in Polish.

---

### Post by cyprys on 2010-05-08
I got mad, uninstalled everything Polish and Poland related. Somehow dictionaries are still in the system and spellchecking works for English as well as Polish.

1. How to change calendar so it would start from Monday?
2. How to change currency so it would show 10.00 PLN or 10.00z&#322;, not 10.00 USD or $10.00?

---

### Post by dagdeniz on 2010-05-08
i tried what you say after i've seen your post; i can confirm you. a bug, maybe? in the "language" tab the in gnome-language-selector, the language that's on the top is supposed the system-wide language. if you keep english on top in "language" tab and choose polish in "text" tab (after clicking apply it system-wide), the currency and the calendar will become Polish, but unfortunately, firefox, open-office and some other apps will be polish, too. however the system will generally be in english. 

note: my menus are in turkish, what i've written are (may be not exact but close) translations

---

### Post by jasontan6 on 2010-05-15
My problem is similar and also related to locales.

I installed Ubuntu in English. Then I installed the German translations. When I changed back to the English translations, some websites like Youtube still load in German. 

The "Language for menus and windows" under the Language tab has "English" at the top of the list, and "Display numbers, dates and currency amounts in the usual format for" is set to "English (United States)". I have also tried clicking on "Apply System-Wide" in both tabs, but it still doesn't work.

---

### Post by cyprys on 2010-05-15
Your browser sends a header which says: "I prefer X language" everytime you open a new webpage. As a temporary workaround you can configure this header's setting in Firefox or Namoroka.

To do so:
1. open a blank page,
2. put "about:config" in address bar,
3. read and confirm the warning (if you agree with what it stands for),
4. find "intl.accept_languages",
5. set it to "en,de" instead of "de,en".

You can use number of settings there. WWW servers will actually interpret "en,de" as "en,de,*" which means: "I prefer English, if it's not accessible then Deutsch, and if it's not accessible then any other language".

---

### Post by jasontan6 on 2010-05-15
> **cyprys said:**
> Your browser sends a header which says: "I prefer X language" everytime you open a new webpage. As a temporary workaround you can configure this header's setting in Firefox or Namoroka.

To do so:
1. open a blank page,
2. put "about:config" in address bar,
3. read and confirm the warning (if you agree with what it stands for),
4. find "intl.accept_languages",
5. set it to "en,de" instead of "de,en".

You can use number of settings there. WWW servers will actually interpret "en,de" as "en,de,*" which means: "I prefer English, if it's not accessible then Deutsch, and if it's not accessible then any other language".

I am using Google Chrome. Firefox loads Youtube in English tho.

---

### Post by cyprys on 2010-05-16
Someone please explain me what the following does so I could submit a decent bug report:

```

export LANG=en_US.UTF-8
export LC_CTYPE=pl_PL.UTF-8
export LC_COLLATE=pl_PL.UTF-8
unset LC_ALL
```
The above does the same as installing and then deleting additional language (like described in my first post).

---

### Post by cyprys on 2010-10-05
Installed 10.10 and problem still persists:

1. I install Ubuntu in English,
2. System -> Administration -> Language Support,
3. it suggests me to install english language packs - which is good,
4. I make sure English (United Kingdom) is selected for menus, interface, etc.,
5. I select ONLY writing aids for Polish,
6. I set date, currency, etc., to be shown in format typical for Poland.

It's all wrong now:
a) calendar starts from Monday, which is good, but it's in polish (Poniedzia&#322;ek, Wtorek, &#346;roda... instead of Monday, Tuesday, Wednesday) which is BAD,
b) update-manager installs packages in Polish or with Polish description (e.g. "Zaawansowana nak&#322;adka na dpkg" for apt),
c) when again in System -> Administration -> Language Support, it tells me I didn't install Polish language packs and help files. I know I didn't - because I don't want it! That's why I selected "Polish writing aids" ONLY,
d) there's still English (United Kingdom) as interface and menus language, yet, it doesn't work (as described in a and b).

---

### Post by cyprys on 2010-10-05
[https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/655427](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/655427)

---

### Post by NothingToSeeHere on 2010-11-05
Thanks for the link to the bug report. I have the same problem (English System, German locale) and the problem described in a comment in the bug report, that Ubuntu overrides my LANG settings in /etc/environment and /etc/default/locale in on every reboot. The fact that firefox completely ignores anything and just started being in English and had to be fixed by explicitly setting it to en via about:config topped all of that.

More interestingly, after I uninstalled German again to try to fix the problem, I couldn't access files containing German characters on an NFSv4 share anymore, so I had to reinstall German translations.

It's good to know that I am not the only one with the locale problem, but the fact that it has existed for some time now worries me if anybody is interested and capable in fixing it.
Although there are still a LOT of bugs in Ubuntu, this one is particularly annoying.

---

### Post by cyprys on 2010-11-06
I can only advice you to distribute the bug report URI among all your friends who experienced the same problem so they could add themselves as individuals affected by the issue - just go to the launchpad link above and click on "This bug affects..." counter and choose "Yes, it affects me". The more people affected, the better chance the bug will be fixed.

---

### Post by NothingToSeeHere on 2010-11-08
Thanks for the advice. I am just wondering why they would implement a system where you could install and use different locales, but it does not seem to be tested.
And why the documentation has those holes, because there is information how to change the locale by editing config files, but there is no information about what software overrides these settings.
Maybe the bug is not directly in the locale system, but at an additional program that just overrides the LANG variable, because it thinks it is smart and thinks people in Germany want LANG=de and that LANG=en_US in the configs could not possibly be want they want ;)

Also, are there different LANG-variables? Cause when I run
```

export LANG="en_US.UTF-8"
googleearth

```
googleearth is in German

but if I run 
```

LANG=en_US googleearth

```
googleearth is in English

does 
```

export LANG="en_US.UTF-8" 

```
have no effect on software, because they somehow still see LANG to be set to german? This somehow seems to be the case, because changing the LANG in the terminal did not interest firefox either (luckily you can override the language setting directly in firefox) 

Just trying to understand how this works (or not works).

EDIT: This seems to be true for every application. While applications are in English and LANG and all LC_ are set to en_US in the configuration files and when running "locale" in the terminal, the applications do not seem to know this.

The calculator uses the German comma instead of the decimal point (ultimately this is what I want, but I do not want it to behave like this if I set all LC_ variables and LANG to en_US.

In Rhythmbox under Edit > Preferences > Music the options under "Preferred format" are in German, although the application itself is in English.

EDIT2: changing the location (System > Administation > Time and Date) has no effect. I set it to somewhere in the USA, but I still get LANG=de_DE and all LC_ set to de_DE on reboot plus the normal problems. This might prove that this is not an "Ubuntu tries to be smart by overriding the locale"-thing, but a real bug.

EDIT3: [COLOR="Red"]**_Possible Solution_**[/COLOR]

It seems that I have fixed all my problems (the wrong LANG setting, googleearth starting in German etc. etc.). The fix was pretty easy. I looked at the environment variables and found that GDM_LANG was incorrectly set to de_DE instead of en_US, cause all I wanted was to set the LC values to german (for time, numbers, etc.).

Therefore I added the following line to the .profile file which was in my home directory

> 
export GDM_LANG="en_US.UTF-8"


and that fixed everything. Somewhere this GDM_LANG was set and then Ubuntu overrides LANG and LC_... values to match the locale of GDM_LANG. Now that the problem was fixed, I tried to have the numbers only in German now, so my .profile had the following lines:

> 
export LANG="en_US.UTF-8"
export LANGUAGE="en_US.UTF-8"
export GDM_LANG="en_US.UTF-8"
export LC_ALL="de_DE.UTF-8"


I logged off and back on and it worked. I have German numbers and time, so that seems to work, Google Earth starts in English as it should (and therefore does not destroy the My Places; but that's another story) and the locale in the Terminal is now set correctly to LANG=en_US and has not been changed magically to "de_DE".
As far as I can tell you right now, you should try setting GDM_LANG explicitly in your profile (or possibly in the default environment, but I have not tested that yet; I am just happy it finally seems to work like I want it to).

---

### Post by LMB on 2011-03-19
Just wanted to add one command to your workaround, or one may run into this error: 

```
bash: warning: setlocale: LC_ALL: cannot change locale de_DE.UTF-8
```The command is: 
```
 sudo locale-gen de_DE.UTF-8
```Now everything works! Thanks.

Edit: almost everything - now the calendar is in German. But at least the calculator uses the comma as decimal separator. Now off to find out how to deal with the same problem in Google Docs

---

### Post by arodulfo on 2012-06-28
Hello, folks!

I want to thank you all for your contribution to this thread.
It has been quite interesting and enriching for me and helped to solve my problem with a 12.04 fresh install I managed to do without paying attention to the language.

I ran into problems with gnome-language-support (or language-support-gnome, like the package name) and was not able to switch my new system to Spanish. Every time I tried to use the mentioned package, I got a crash report and no change at all.

I used NothingToSeeHere's latest hints and everthing went smooth after reboot.
Kudos! to him, and my deepest respect.:cool:

Following cyprys' advice, I will also visit the thread in the launchpad to help pressing out so that this annoying problem gets attention enough to be solved ASAP.

Kind regards from Spain,:p

---

