---
title: "How can I install and remove fonts (OpenType, TrueType)"
date: 2011-05-28
forum: General Help
---

### Post by stellaong on 2011-05-28
I can't manage to find the fonts directory in Ubuntu. The fonts directory is much more conspicuous in Windows OS. Since I am a web designer, I love to experiment with a spectrum of fonts ornately expressed. I have migrated from Windows to Ubuntu because I am very impressed by its organization and functionality (sadly I couldn't download Ubuntu 11 due to internet connection errors. Moreover ShipIt had terminated).

Can anyone kindly give me the instructions to install and remove fonts in Ubuntu 10.10? I couldn't find any simple manual for this purpose online. Thank you so much for your help!

---

### Post by JRV on 2011-05-28
There are fonts in the Software Center.

If you need to install manually:
> There are various locations in GNU/Linux in which fonts can be kept. These locations are defined in /etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and /home/<username>/.fonts (where <username> is your user name).

The easiest way to install a truetype font is to press alt-F2 and enter the following code (this will open nautilus in the right directory):

gksu nautilus /usr/share/fonts/truetype

Then create a new directory, name the directory whatever you like (choose a name that you remember if you ever need to backup your fonts personal fonts). Copy the fonts into that directory and finally rebuild the font information files by pressing alt-F2, mark 'run in terminal' so you can see the progress and entering the following code:

sudo fc-cache -f -v

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

gksudo nautilus fonts:


---

### Post by hawthornso23 on 2011-05-28
... or you can just double click the ttf file and it'll ask you if you want to install it.

---

