---
title: "Alt-Tab and Workspaces not working"
date: 2010-10-11
forum: General Help
---

### Post by readeemer on 2010-10-11
Hi all,

(I'm new to the forums and not very good with Ubuntu so I apologise if I do something stupid ^^')

I recently installed Ubuntu 10.10 on my laptop. I've got access to both the Netbook Edition and the Desktop Edition, so I tried booting into the Desktop Edition since I prefer to use this.

Within it, I cannot use Alt-Tab to move between multiple windows. I don't have access to *moving* between workspaces; :confused: rather weirdly, I can move a window to a different workspace by right clicking on the application and selecting to move it to a different workspace but I cannot use Ctrl-Alt-Right or Left to move between workspaces, nor can I use Ctrl-Alt-Shift-Left or Right to move a window from one workspace to another.

I have checked the Keyboard Shortcuts under the System->Preferences side. Alt-Tab, Ctrl-Alt-Right/Left and Ctrl-Alt-Shift-Right/Left are all set as the commands for Moving between Windows using the popup window, moving to the right/left workspace and moving a window to the right/left workspace respectively.

I've seen a lot of people saying that they have problems when they've got compiz installed and alt-tab causes problems with this, but I don't have compiz installed.

Since I used sudo apt-get upgrade -d from my old 10.04 Netbook Edition, am I missing packages to correctly run the Desktop Edition? Or have I done something very stupid? I would really appreciate any help I could get on this matter.

Thank you,
~read

Note: Within the Netbook Edition, I can use multiple workspaces and Alt-Tab does work, but the UI is very slow and causes the system to lag whenever I open an application. :(

---

### Post by ubunterooster on 2010-10-11
A complete guess but try using the *other* Ctrl and other Shift Key. I had this problem once but it was specific to one Ctrl key and one Shift key

---

### Post by readeemer on 2010-10-11
Hi ubunterooster,

I've just tried using the other set of Ctrl and Shift keys.  There was no change in the behaviour of the system...^^'

Thanks for the suggestion though :)

~read

---

### Post by readeemer on 2010-10-12
Hi all,

One of my friends managed to help me solve this during the afternoon.  (Due to my inexperience with Ubuntu) I uninstalled compiz and as a result disabled my Window switching and Workspace switching, so a lot of my window management was gone.

To fix this we reinstalled compiz and compizconfig-settings-manager and re-enabled the window and workspace switchers.

Thanks to any who happened to look at this problem and I hope it will help anyone who happens to perform the same blunder I did :P

~read

---

