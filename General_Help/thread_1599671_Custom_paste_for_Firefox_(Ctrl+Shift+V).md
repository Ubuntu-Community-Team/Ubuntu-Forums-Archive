---
title: "Custom paste for Firefox (Ctrl+Shift+V)"
date: 2010-10-18
forum: General Help
---

### Post by Virus666 on 2010-10-18
Hi all,

Is there any way to paste texts without formating in **Firefox**? Normally, I'm using **Ctrl+Shift+V** shortcut in **OpenOffice.org**; and now **Google Chrome** has the same function:

[http://chrome.blogspot.com/2010/09/tip-just-text-please.html#links](http://chrome.blogspot.com/2010/09/tip-just-text-please.html#links)

I found **Copy Plain Text** and **Extended Copy Menu** add-ons for custom copy but I still could not find a compatible add-on for custom paste.

[https://addons.mozilla.org/en-US/firefox/addon/134/](https://addons.mozilla.org/en-US/firefox/addon/134/)
[https://addons.mozilla.org/en-US/firefox/addon/4554/](https://addons.mozilla.org/en-US/firefox/addon/4554/)

An universal solution for both Linux, Mac and Windows would be wonderful...

---

### Post by lovinglinux on 2010-10-18
What exactly do you want? I could write the extension for you.

---

### Post by Virus666 on 2010-10-19
@lovinglinux

Really? I just want to paste texts to Firefox without formating (paste as plain text.) You can do such thing in OpenOffice.org via Ctrl+Shift+V shortcut.

If Google Chrome has that function, there can be no reason for Firefox to not to have it:

[http://www.ditii.com/2010/09/15/google-chrome-adds-ctrl-shift-v-shortcut-for-paste-as-plain-text/](http://www.ditii.com/2010/09/15/google-chrome-adds-ctrl-shift-v-shortcut-for-paste-as-plain-text/)

I have checked **about:config** prefences but there is nothing related to my need. Maybe an extension or script which

- Automaticly opens a text editor (Gedit, Kate, TextEdit, Notepad, ...)
- Pastes the text to text editor
- Cuts the text
- Closes the text editor
- Pastes the unformatted text to Firefox

via Ctrl+Shift+V can make it.

I have tottally no idea about coding or software designing as you see, but that kind of feature definitely improves usability of Firefox.

Thank you...

---

### Post by lovinglinux on 2010-10-19
> **Virus666 said:**
> @lovinglinux

Really? I just want to paste texts to Firefox without formating (paste as plain text.) You can do such thing in OpenOffice.org via Ctrl+Shift+V shortcut.

If Google Chrome has that function, there can be no reason for Firefox to not to have it:

[http://www.ditii.com/2010/09/15/google-chrome-adds-ctrl-shift-v-shortcut-for-paste-as-plain-text/](http://www.ditii.com/2010/09/15/google-chrome-adds-ctrl-shift-v-shortcut-for-paste-as-plain-text/)

I have checked **about:config** prefences but there is nothing related to my need. Maybe an extension or script which

- Automaticly opens a text editor (Gedit, Kate, TextEdit, Notepad, ...)
- Pastes the text to text editor
- Cuts the text
- Closes the text editor
- Pastes the unformatted text to Firefox

via Ctrl+Shift+V can make it.

I have tottally no idea about coding or software designing as you see, but that kind of feature definitely improves usability of Firefox.

Thank you...

I guess that complicates things a little bit. You want to paste text copied from elsewhere, like OpenOffice, into a Firefox form field, right, not the other way (Firefox to OpenOffice)?

Would be enough if you paste with the formatting, then select the text and click a button to remove the formatting?

---

### Post by Virus666 on 2010-10-19
Yeah, I just want to paste text INTO Firefox FROM elsewhere. But my point is to get rid of the format of the text. OpenOffice.org was just an example; we can paste text without formating TO OpenOffice.org via Ctrl+Shift+V shortcut. Same act for Firefox would me nice... :)

---

### Post by lovinglinux on 2010-10-19
> **Virus666 said:**
> Yeah, I just want to paste text INTO Firefox FROM elsewhere. But my point is to get rid of the format of the text. OpenOffice.org was just an example; we can paste text without formating TO OpenOffice.org via Ctrl+Shift+V shortcut. Same act for Firefox would me nice... :)

I will look into it.

---

### Post by lovinglinux on 2010-10-19
It seems to me the formatting depends on the form you are pasting to. For example lets consider the following text:

[LIST]
[*]this is a text
[*]this is a text
[*]this is a text
[/LIST]

When I copy it from this site and paste on Gmail, it is formatted exactly like you see it.

[LIST]
[*]this is a text
[*]this is a text
[*]this is a text
[/LIST]

If I select the "Plain Text" option on Gmail, it is pasted as code:

[noparse][LIST][/noparse]
[noparse][*]this is a text[/noparse]
[noparse][*]this is a text[/noparse]
[noparse][*]this is a text[/noparse]
[noparse][/LIST][/noparse]

If I paste the same text here in the forum, it is formatted like this:

    this is a text
    this is a text
    this is a text

I was starting to build the extension, but it doesn't work as I expected.

    this is a text
    this is a text
    this is a text

So I guess I would need to strip the formatting elements instead of pasting as plain text. This will take some time.

---

### Post by Virus666 on 2010-10-19
I am thank you for all your efforts to solve this problem. You're so helpful... :) 

The method that I suggested before may be easier; using a script which automaticly does the jon via a text editor...

Good luck... :P

---

### Post by lovinglinux on 2010-10-19
> **Virus666 said:**
> I am thank you for all your efforts to solve this problem. You're so helpful... :) 

The method that I suggested before may be easier; using a script which automaticly does the jon via a text editor...

Good luck... :P

I guess so. You can try [xclip](apt:xclip).

---

### Post by lovinglinux on 2010-10-19
> **Virus666 said:**
> Yeah, I just want to paste text INTO Firefox FROM elsewhere. But my point is to get rid of the format of the text. OpenOffice.org was just an example; we can paste text without formating TO OpenOffice.org via Ctrl+Shift+V shortcut. Same act for Firefox would me nice... :)

I just tried CTRL+Shift+V in both OO and Firefox and they do the same thing. They paste unformatted text like this:

> When I copy it from this site and paste on Gmail, it is formatted exactly like you see it.

        this is a text
        this is a text
       this is a text

I don't think building an extension would be very useful in this case, unless you don't want the extra spaces and want all lines aligned to the left.

---

### Post by Virus666 on 2010-10-22
So, it seems that all I can do is to use [Extended Copy Menu]("https://addons.mozilla.org/en-US/firefox/addon/4554/") extension for Firefox. But, it would be nice to use it as **CTRL+SHIFT+C** at least... It's a bit hard to make **CTRL+ALT+C **with single hand... :)

Anyway, thanks for helping... :roll:

---

### Post by lovinglinux on 2010-10-22
> **Virus666 said:**
> It's a bit hard to make **CTRL+ALT+C **with single hand... :)

Indeed :)

---

### Post by Murz on 2012-09-05
Virus666, did you find any solution for this problem?

We need **Paste as PlainText**, not Copy as PlainText feature, because we pasting text from other that firefox apps.

---

