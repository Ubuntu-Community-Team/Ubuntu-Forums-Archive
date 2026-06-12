---
title: "Background color for tty consoles"
date: 2012-05-25
forum: General Help
---

### Post by delfick on 2012-05-25
Hello,

Is it possible to make the tty consoles (I'm talking about the ones you get to via ctrl+alt+f1-6) use a black on white color scheme?

Thankyou

Stephen.

---

### Post by jerome1232 on 2012-05-25
use the command setterm to change the color.
ie for your example

```
setterm -foreground black -background white
```

If you want it to happen automatically I suppose you could put it in your ~/.bashrc or ~/.profile

---

### Post by delfick on 2012-05-25
unfortunately that one doesn't seem to work.

I'm on Ubuntu 12.04 if that makes a difference....

---

### Post by cortman on 2012-05-25
I believe this requires a kernel patch. A bit of info [here.]("http://www.linuxforums.org/forum/miscellaneous/144645-change-boot-tty-colors.html#post691996")

---

### Post by jerome1232 on 2012-05-25
You  have to run it in a tty

---

### Post by mlentink on 2012-05-25
It's a bit easier than that...

Open up a terminal (click on the dash, start typing term ... etc) In the top menu, select Edit> Profile Preferences.

You can set a background color, background picture or even transparency. Edit to your heart's desire

---

### Post by jerome1232 on 2012-05-25
> **mlentink said:**
> It's a bit easier than that...

Open up a terminal (click on the dash, start typing term ... etc) In the top menu, select Edit> Profile Preferences.

You can set a background color, background picture or even transparency. Edit to your heart's desire

That is not a tty, that is a pts

---

### Post by mlentink on 2012-05-25
> **jerome1232 said:**
> That is not a tty, that is a pts

<Stuffs socks in mouth> Uhmm. Should have read better.

---

### Post by delfick on 2012-05-25
> **cortman said:**
> I believe this requires a kernel patch. A bit of info [here.]("http://www.linuxforums.org/forum/miscellaneous/144645-change-boot-tty-colors.html#post691996")

Well in that case I'l settle for making the text white instead of black.

```

# In ~/.zshrc

autoload -U colors && colors
function prompt_color {
    # Make sure text in tty is white on the black background
    # Cause changing the background seems difficult :(
    case $TTY in
        /dev/tty[1-9]|/dev/tty[012][0-9])
            echo %{$fg[white]%}
            ;;
        *)
            echo %{$fg[black]%}
            ;;
    esac
}

```

and I added that to the end of my Prompt

---

