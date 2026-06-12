---
title: "How to post from the Terminal."
date: 2010-11-07
forum: General Help
---

### Post by Coda_ on 2010-11-07
When someone asks me to post some code from the terminal, is there a way to copy it? As opposed to having to type it all out? Newb question, I know, but I didnt see it addressed anywhere else.

---

### Post by junapp on 2010-11-07
> **Coda_ said:**
> When someone asks me to post some code from the terminal, is there a way to copy it? As opposed to having to type it all out? Newb question, I know, but I didnt see it addressed anywhere else.
I think if you select it it is copied automatically (paste with middle click), or select, then use Ctrl+Insert, or Edit->copy, or right click and copy. Then back here in the forum, use the code tags and paste (Right click -> Paste, or Shift+Insert, or Ctrl-V)  The code tags are available by clicking the little # sign in the buttons just above where you type, or by typing the word code in square brackets, and /code to end (also in square brackets)

---

### Post by Quackers on 2010-11-07
There are a few ways.
The first is to put your cursor at the start of what you wish to copy (to the clipboard) and press and hold the left click button and drag the cursor to the last bit of what you want to copy. This will highlight all the text you want to copy. Right-click any area of the highlighted text and select "copy" then go to your post and if you want to use code tags (sometimes that's best, if it's a lot of text) click on New Reply and then on the # symbol in the toolbar. This will create 2 CODE tags and the cursor will be flashing in between them. Right-click the cursor then select paste, and you're done. 
If you don't want code tags just paste it direct into the post.
You can also use ctrl + C to copy and ctrl + V to paste (ctrl+shift+V to paste into a terminal window - or just use the middle mouse button).

---

### Post by Coda_ on 2010-11-07
Thanks. I never thought to simply right click. I just assumed it would be some complicated process.

---

### Post by efflandt on 2010-11-07
If you are using an xterm (terminal in gnome or whatever) the Ctrl+C hotkey is likely not enabled.  But if you highlight text and either right click and select Copy, or Copy using Edit menu of terminal you should be able to copy it.  Then Ctrl-V to paste it into your browser.

Of course if you are have trouble getting into X and are at a text console you will need to redirect output to a file.  For example:

```
sudo lspci -v > lspci.txt
```Then if you put lspci.txt where you can access it or booted from a live CD you could open it with a text editor to copy/paste it.

If there is an error message you need to capture, you can redirect stderr to stdout to get it to the file:

```
broken_command > output.txt 2>&1
```

---

