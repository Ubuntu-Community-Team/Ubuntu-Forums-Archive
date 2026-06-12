---
title: "Setting Vim as default text editor"
date: 2010-07-13
forum: General Help
---

### Post by imple on 2010-07-13
Hi,

I'd like to set Vim as my default text editor (so it opens when I click a file). How can I do this?

Thanks,
Ben

---

### Post by Jazzy_Jeff on 2010-07-13
You should be able to right click on a file and go to preferences and click on the open with tab.

---

### Post by imple on 2010-07-13
I've tried: open with -> other application -> custom command -> "vim", but that doesn't seem to work.

---

### Post by jwbrase on 2010-07-13
> **imple said:**
> Hi,

I'd like to set Vim as my default text editor (so it opens when I click a file). How can I do this?

Thanks,
Ben

Do you mean the text-mode version or the GUI version?

---

### Post by imple on 2010-07-13
The text-mode version.

---

### Post by WorMzy on 2010-07-13
You'll need to set a custom command for it to open with, something like 'gnome-terminal -x vim'. I'm not on Linux at the moment, but I think that should work.

---

### Post by imple on 2010-07-13
Gnome-terminal doesn't seem to take any arguments.

---

### Post by WorMzy on 2010-07-13
It definitely does, I've used a similar command to launch weechat-curses (a CLI-based IRC client) from my applications menu. Check 'man gnome-terminal', it might be -e instead of -x.

EDIT: Hold on, I'll boot into one of my Linux installations and see exactly how I've done it.

---

### Post by Pogeymanz on 2010-07-13
I do believe the command is:
gnome-terminal -e vim

---

### Post by WorMzy on 2010-07-13
It is -e COMMAND, but it doesn't seem to work as an application launcher. My experiments with vi, vim and nano just open a new buffer instead of opening the exiting document for editing. :/

I think that this is the right line of thought, but I'm not sure how you'd get it to load the document.

EDIT: You can create a custom launcher on gnome-panels for vim as an "Application in terminal", and drag text files into it, so there must be a way to get custom application launching commands to read files into them..

---

### Post by gsgleason on 2010-07-13
Do you want to use vim in a terminal or the gvim gui?

---

### Post by WorMzy on 2010-07-13
Got it.

Create a new document in your ~ folder, called "vimlaunch" (or something like that), open it and add the following content:
```
#!/bin/sh

gnome-terminal -e "vim $1"
```

Make it executable by running
```
chmod +x ~/vimlaunch
```
Optionally, move it to /usr/bin with
```
sudo mv ~/vimlaunch /usr/bin
```

Then right-click on a text file, choose properties, open with, and add a new custom command:
```
'/home/USERNAME/vimlaunch' #if you left it where you made it
```
or
```
vimlaunch #if you moved it to /usr/bin
```

Voila.

---

### Post by imple on 2010-07-13
Thanks. I've done as you said. When I test it, a terminal window pops up momentarily before disappearing. However, it works when I test it with "vimlaunch test.txt". What's going wrong?

---

### Post by WorMzy on 2010-07-13
I'm not sure. It works almost* perfectly for me on both Arch Linux and Ubuntu 9.10, so it should work fine on other Linux distros without any issues. You could try changing "#!/bin/sh" to "#!/bin/bash", either works fine for me.

*It doesn't like filenames with spaces in their names, but changing the file's content to:
```
#!/bin/sh

gnome-terminal -e "vim \"$1\""

```

fixes it.

Of course, this isn't much use to you if it doesn't work in the first place. Try changing sh to bash first and see if that makes any difference.

---

### Post by rocksockdoc on 2010-08-26
IMHO, it should be easier to figure out how to change the default text editor to vim or vi.

I too failed when I tried changing the default associations for text files by right clicking on a *.txt file in the file browser and then selecting "Open with other application", and then selecting either "vim.nox" or "Use a custom command". Likewise, I failed to set the default editor to vim or vi using the right-click "Properties" form, and selecting the "Open with" tab and then selecting "vim.nox".

I just tried this:
```

$ sudo aptitude install vim-nox

$ which {vi,vim,vim.nox}
/usr/bin/vi
/usr/bin/vim
/usr/bin/vim.nox

$ sudo update-alternatives --config editor
Reported:
There are 4 choices for the alternative editor (providing /usr/bin/editor).
  Selection    Path              Priority   Status
------------------------------------------------------------
* 0           /bin/nano            40         auto mode
  1            /bin/ed             -100        manual mode
  2            /bin/nano            40        manual mode
  3            /usr/bin/vim.nox  40        manual mode
  4            /usr/bin/vim.tiny  10        manual mode
Press enter to keep the current choice
[*], or type selection number:

I was surprised neither "vi" nor "vim" showed up; only vim.nox was available of the 3.
I selected number #3 as being the closest to a vi that was available.

This reported:
 update-alternatives: using /usr/bin/vim.nox to provide /usr/bin/editor (editor) in manual mode.

```

But, even so, when I doubleclicked on a *.txt file, nothing happened.

Can someone clarify how to change the default text editor for *.txt files to vi or vim?

---

