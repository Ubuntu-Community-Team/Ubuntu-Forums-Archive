---
title: "moving &quot;logout&quot; icon from bottom panel to 2-nd panel?"
date: 2012-03-09
forum: General Help
---

### Post by verbertus on 2012-03-09
Hi all,

Happily running **L**ubuntu 12.04 beta1, I tried to add the logout icon ('system-shutdown-icon') to a second -vertical- panel.

I started by removing the one in the bottom panel, thinking it would thereby become available "on the right side" of the second panel's editor. No it didn't :(

A picture showing where I want the icon to appear, my 2-nd panel to the right side of the screen. (I know I'm weird, but I like this setup. It feels ergonomical and much more logical on my widescreen, compared to the left, or 'unity' side ;) ):

[IMG]http://i.imgur.com/37EUD.png[/IMG]

Any help would be much appreciated!

---

### Post by ajgreeny on 2012-03-09
Interesting question!

The logout icon in Lubuntu on the far right hand end of the bottom panel is contained in an application lunchbar, which I once removed from a test-bed install of Lubuntu, and I could find no way to add back as the logout applet does not seem to be in the full list of available additions.

I am sure there must be a way to do it, which neither of us is aware of, but I will keep an eye on this thread to see if an answer is forthcoming or not.

PS:  Did you try to move just the icon or the whole application launchbar?  I'm not sure even if that would help, as I do not know if you can drag the launchbar from panel to panel.  There is however a plain text file called ~/.config/lxpanel/Lubuntu/panels/panel which in its default is as shown in the attached file, now named panel.txt.  See if that gives you any clues.
```
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
    edge=bottom
    allign=left
    margin=0
    widthtype=percent
    width=100
    height=24
    transparent=0
    tintcolor=#000000
    alpha=0
    autohide=0
    heightwhenhidden=2
    setdocktype=1
    setpartialstrut=1
    usefontcolor=1
    fontcolor=#ffffff
    background=1
    backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
    iconsize=22
}

Plugin {
    type = menu
    Config {
        image=/usr/share/lubuntu/images/lubuntu-logo.png
        system {
        }
        separator {
        }
        item {
            command=run
        }
        separator {
        }
        item {
            image=gnome-logout
            command=logout
        }
    }
}

Plugin {
    type = launchbar
    Config {
        Button {
            id=/usr/share/applications/pcmanfm.desktop
        }
        Button {
            id=/usr/share/applications/lxterminal.desktop
        }
        Button {
            id=/usr/share/applications/firefox.desktop
        }
        Button {
            id=/usr/share/applications/abiword.desktop
        }
        Button {
            id=/usr/share/applications/gnumeric.desktop
        }
        Button {
            id=/usr/share/applications/synaptic.desktop
        }
    }
}

Plugin {
    type = space
    Config {
        Size=4
    }
}

Plugin {
    type = wincmd
    Config {
        image=window-manager
        Button1=iconify
        Button2=shade
        Toggle=0
    }
}

Plugin {
    type = space
    Config {
        Size=4
    }
}

Plugin {
    type = pager
}

Plugin {
    type = space
    Config {
        Size=4
    }
}

Plugin {
    type = taskbar
    expand=1
    Config {
        tooltips=1
        IconsOnly=0
        ShowAllDesks=0
        UseMouseWheel=1
        UseUrgencyHint=1
        FlatButton=0
        MaxTaskWidth=150
        spacing=1
        GroupedTasks=0
    }
}

Plugin {
    type = volumealsa
}

Plugin {
    type = tray
}

Plugin {
    type = dclock
    Config {
        ClockFmt=%a %e %b %H:%M
        TooltipFmt=%A %x
        BoldFont=0
        IconOnly=0
    }
}

Plugin {
    type = launchbar
    Config {
        Button {
            id=lubuntu-logout.desktop
        }
    }
}

```

---

### Post by verbertus on 2012-03-09
Thank you ajgreeny!

To answer your question: I simply tried to move the logout icon by removing it from the bottom panel, without removing the application bar.

The icon cannot be added to the second 'top' panel, nor added back to the bottom one. It just disappears :frown:

I had already tried editing the panel file several times. After some tries, I was sure I had made no syntaxis mistakes and came to the conclusion something is overriding the text file.

I wonder if the logout icon is not part of some "systembox", just like the network icon, meaning it is by default not editable.

I also searched the lxde wiki, followed some advice  I hardly understood and froze lxpanel..

Let's hope one of the lxde gurus will read this..and enlighten us :)

Thanks again.

---

### Post by SteveDee on 2012-03-09
> **verbertus said:**
> ...I tried to add the logout icon ('system-shutdown-icon') to a second -vertical- panel...

See: [http://ubuntuforums.org/showthread.php?t=1934101](http://ubuntuforums.org/showthread.php?t=1934101)

---

### Post by verbertus on 2012-03-09
Yes! That worked!

I had done exactly the same as you propose, but without restarting Lubuntu...As I saw no effect, I deleted my changes to the text file, so never saw a result after restarting :)

Looking good:

[IMG]http://i.imgur.com/MVpHu.png[/IMG]

T**hank You SteveDee!!!**

---

