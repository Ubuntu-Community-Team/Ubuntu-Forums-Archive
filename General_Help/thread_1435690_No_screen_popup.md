---
title: "No screen popup"
date: 2010-03-21
forum: General Help
---

### Post by satimis on 2010-03-21
Hi folks,

Ubuntu 9.10 64bit

On running;
# dpkg-reconfigure locales```

Generating locales...
  bn_BD.UTF-8... up-to-date
  bn_IN.UTF-8... up-to-date
  de_AT.UTF-8... up-to-date
  de_BE.UTF-8... up-to-date
  de_CH.UTF-8... up-to-date
  de_DE.UTF-8... up-to-date
  de_LI.UTF-8... up-to-date
  de_LU.UTF-8... up-to-date
.....

```

no screen popup to make selection.  Please advise how to popup the screen?  TIA


B.R.
satimis

---

### Post by dcstar on 2010-03-21
> **satimis said:**
> Hi folks,

Ubuntu 9.10 64bit

On running;
# dpkg-reconfigure locales```

Generating locales...
  bn_BD.UTF-8... up-to-date
  bn_IN.UTF-8... up-to-date
  de_AT.UTF-8... up-to-date
  de_BE.UTF-8... up-to-date
  de_CH.UTF-8... up-to-date
  de_DE.UTF-8... up-to-date
  de_LI.UTF-8... up-to-date
  de_LU.UTF-8... up-to-date
.....

```

no screen popup to make selection.  Please advise how to popup the screen?  TIA

B.R.
satimis

What selection?, what do you actually want to do?, all that command does is run the package scripts for installing/checking the locale files.

If you want to change things, the system default locale is at: /etc/default/locale

---

### Post by lidex on 2010-03-21
> **satimis said:**
> Hi folks,

Ubuntu 9.10 64bit

On running;
# dpkg-reconfigure locales```

Generating locales...
  bn_BD.UTF-8... up-to-date
  bn_IN.UTF-8... up-to-date
  de_AT.UTF-8... up-to-date
  de_BE.UTF-8... up-to-date
  de_CH.UTF-8... up-to-date
  de_DE.UTF-8... up-to-date
  de_LI.UTF-8... up-to-date
  de_LU.UTF-8... up-to-date
.....

```

no screen popup to make selection.  Please advise how to popup the screen?  TIA


B.R.
satimis

If you're looking for a gui to change language settings, try ""System>Administration>Language Support"

---

### Post by satimis on 2010-03-21
> **lidex said:**
> If you're looking for a gui to change language settings, try ""System>Administration>Language Support"

Hi lidex,

Thanks for your advice.


On;
-> Administration -> Language Support
it popup:```


The language support is not installed completely

```
-> install

installing 25 language packages

# dpkg-reconfigure locales
still displays a list of languages NOT GUI window for selecting language.

On;
-> Administration -> Language Support

I can't select multiple languages NOR *.UTF-8


B.R.
satimis

---

### Post by lidex on 2010-03-22
> **satimis said:**
> Hi lidex,

Thanks for your advice.


On;
-> Administration -> Language Support
it popup:```


The language support is not installed completely

```
-> install

installing 25 language packages

# dpkg-reconfigure locales
still displays a list of languages NOT GUI window for selecting language.

On;
-> Administration -> Language Support

I can't select multiple languages NOR *.UTF-8


B.R.
satimis

You're supposed to drag them into the order of preference. Click the systemwide button and logout. dpkg is not what you want.

---

### Post by satimis on 2010-03-22
> **lidex said:**
> You're supposed to drag them into the order of preference. Click the systemwide button and logout. dpkg is not what you want.

On the login page
language selected = English (United States)

I can't find *.UTF-8 there


satimis

---

### Post by lidex on 2010-03-22
> **satimis said:**
> On the login page
language selected = English (United States)

I can't find *.UTF-8 there


satimis

I believe the character encoding default is utf-8 in ubuntu now.

---

### Post by satimis on 2010-03-23
> **lidex said:**
> I believe the character encoding default is utf-8 in ubuntu now.

Noted and thanks

B.R.
satimis

---

