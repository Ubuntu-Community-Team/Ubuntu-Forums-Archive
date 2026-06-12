---
title: "Where do I install fonts for desktop themes?"
date: 2010-05-27
forum: General Help
---

### Post by 3pinner on 2010-05-27
Had to download some fonts for the desktop theme Crux.
What folder do they go in? fonts? In with the themes?
Thanks

---

### Post by linuxman94 on 2010-05-27
From the ubuntu wiki:

> Manually

There are various locations in GNU/Linux in which fonts can be kept. These locations are defined in /etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and /home/<username>/.fonts (where <username> is your user name).

The easiest way to install a truetype font is to press alt-F2 and enter the following code (this will open nautilus in the right directory):

```
gksu nautilus /usr/share/fonts/truetype
```

Then create a new directory, name the directory whatever you like (choose a name that you remember if you ever need to backup your fonts personal fonts). Copy the fonts into that directory and finally rebuild the font information files by pressing alt-F2, mark 'run in terminal' so you can see the progress and entering the following code:
```

sudo fc-cache -f -v
```

<!> Note: After you install a new font, you will need to make sure that programs in which you want to use the new fonts can recognize them. In most cases this is done by closing and reopening the programs; however, some programs may require you to log out and log back in.

The easiest place for people to put their fonts is /home/<username>/.fonts. If you have not already done so, create this folder:

    * Open your home folder in Nautilus (GNOME) or Konqueror (KDE).
    * Since dot-folders are really hidden folders, you need to choose "Show Hidden Files" from the View menu.
    *

      Go to File -> Create Folder (GNOME), or right-click and choose Create New -> Folder (KDE).
    * Name the new folder ".fonts". 

Now double click on the folder to open it, and drag and drop your fonts into the folder.

On GNOME, you can also directly open the virtual folder fonts:/ (within a Nautilus window, choose Go -> Location or press Ctrl+L) and drag and drop fonts into this folder. (Does not work in in Hardy Heron 8.04 due to changes. Please follow the method above.)

However, fonts that are added by either of the ways above will only be available for one user. To make them available system-wide, drag and drop them to the directory /usr/share/fonts. (Note: If you're on Kubuntu you may have to cd to /usr/share/fonts and run mkfontscale, mkfontdir, fc-cache after this. See the instructions below.)

As in the last method, on GNOME you can also add fonts directly to fonts:/. However, you must open the virtual folder as root. You can do this by opening a terminal window and running

```
gksudo nautilus fonts:
```
[URL="https://wiki.ubuntu.com/Fonts"]
https://wiki.ubuntu.com/Fonts[/URL]

---

