---
title: "How to check for dependencies?"
date: 2012-07-02
forum: General Help
---

### Post by cogset on 2012-07-02
This will sound very dumb,however I need to know how do I  check if a series of required packages is already installed before installing/compiling a program:let's say I want to know if for instance these packages```
 libjpeg62  libtiff4-dev libpng12-dev zlib1g-dev libbz2-dev liblcms2-dev  libexiv2-dev 
``` are already on my system,how do I (quickly) check?
I was thinking about** dpkg --status** or** dpkg --list**,but then I think they must be combined with some other command (grep ?) to check for all in one go,is that correct? Or maybe I should use a different command altogether? I guess there must be an easy solution,it just escapes me.

---

### Post by cortman on 2012-07-02
> **cogset said:**
> This will sound very dumb,however I need to know how do I  check if a series of required packages is already installed before installing/compiling a program:let's say I want to know if for instance these packages```
 libjpeg62  libtiff4-dev libpng12-dev zlib1g-dev libbz2-dev liblcms2-dev  libexiv2-dev 
``` are already on my system,how do I (quickly) check?
I was thinking about** dpkg --status** or** dpkg --list**,but then I think they must be combined with some other command (grep ?) to check for all in one go,is that correct? Or maybe I should use a different command altogether? I guess there must be an easy solution,it just escapes me.

Try

```
dpkg --get-selections | grep package_name
```

---

### Post by cogset on 2012-07-02
Thanks;),eventually after your suggestion I've found that both  **dpkg --get-selections **and** dpkg --list **work indeed just fine (the latter is a bit more verbose),no need at all to pipe it through  grep for my needs,if anything attempting to pipe all the package names through grep invalidates the search.

---

### Post by cortman on 2012-07-02
> **cogset said:**
> Thanks;),eventually after your suggestion I've found that both  **dpkg --get-selections **and** dpkg --list **work indeed just fine (the latter is a bit more verbose),no need at all to pipe it through  grep for my needs,if anything attempting to pipe all the package names through grep invalidates the search.

You can do it that way. Grep is handy for matching patterns, if you need to use a regex.
I must say I've never had it invalidate a search.

```
cortman-VirtualBox% sudo dpkg --get-selections | grep emacs
emacs23-bin-common				install
emacs23-common					install
emacs23-nox					install
emacsen-common					install
```

---

### Post by cogset on 2012-07-04
> **cortman said:**
> You can do it that way. Grep is handy for matching patterns, if you need to use a regex.
I must say I've never had it invalidate a search.
[CENTER]
[/CENTER]
 

I meant that if I were to grep for a string like that 
```

[LEFT] libjpeg62  libtiff4-dev libpng12-dev zlib1g-dev
 libbz2-dev liblcms2-dev  libexiv2-dev [/LEFT]

```[LEFT] I didn't know how do properly do it,therefore getting an invalid result:now I reckon that an expression like this ```
dpkg --list |grep -E  " libjpeg62\ |libtiff4-dev\
 |libpng12-dev\ |zlib1g-dev\ |libbz2-dev\ |liblcms2-dev\ |libexiv2-dev "

```[/LEFT]
actually works,but then I realized that simply using dpkg --list or dpkg --get-selections as suggested and then input all the dependencies names does just the same thing and it's faster ;)

---

### Post by cortman on 2012-07-04
> **cogset said:**
> I meant that if I were to grep for a string like that 
```

[LEFT] libjpeg62  libtiff4-dev libpng12-dev zlib1g-dev
 libbz2-dev liblcms2-dev  libexiv2-dev [/LEFT]

```[LEFT] I didn't know how do properly do it,therefore getting an invalid result:now I reckon that an expression like this ```
dpkg --list |grep -E  " libjpeg62\ |libtiff4-dev\
 |libpng12-dev\ |zlib1g-dev\ |libbz2-dev\ |liblcms2-dev\ |libexiv2-dev "

```[/LEFT]
actually works,but then I realized that simply using dpkg --list or dpkg --get-selections as suggested and then input all the dependencies names does just the same thing and it's faster ;)

Actually, a smarter way to grep for that would be to use the or pipe |.
Regular expressions are fascinating.

```
sudo dpkg --get-selections | grep -E "emacs|vi|nano"
```

---

