---
title: "Stupid yellow lines with text."
date: 2010-02-22
forum: General Help
---

### Post by colobix on 2010-02-22
Hey.
HOw do I get rid of the yellow lines with text that pops up everytime I'm holding the mouse over something?
I find them to be VERY annoying.
So please help me here.
Thanks in advance

---

### Post by mcduck on 2010-02-22
Tooltips?

The simple, answer is no, you can't get rid of them.

..and the complicated answer is that if you use Compiz (the "desktop effects"), you can make the tooltips invisible. Just enable the "Opacity, Brightness and Saturation"-plugin, go to Opacity-tab, add "type=tooltip" to the list and set it's opacity to 0.

---

### Post by tacantara on 2010-02-22
Are you referring to the "tool tips" that pop-up when you mouse over items in programs?

---

### Post by colobix on 2010-02-22
> **tacantara said:**
> Are you referring to the "tool tips" that pop-up when you mouse over items in programs?
Yes. It's the most annoying thing. I wish I could turn it off somehow.
That compiz this was too complicated. I understand the plugin part but after I have enabled the plugin, what do I do next?
And is that the only way to solve this problem?

---

### Post by tacantara on 2010-02-22
Here's a little trick you can try to get rid of those tooltips: Open a terminal (Applications-->Accessories-->Terminal) and enter **gconf**;  in it go to  "apps-->panel-->global" and almost at the bottom  there's an option called "tooltips_enabled". Just uncheck the box.

You can also access gconf by pressing ALT+F2, then enter gconf-editor in the box.  Press enter to run gconf, then follow the instructions above to navigate to the tooltips_enabled box.

---

### Post by colobix on 2010-02-22
when I type gconf it says command not found.
I even tried sudo gconf just in case.

---

### Post by tacantara on 2010-02-22
If you use the ALT+F2 method to open up the Run Application window, enter "gconf-editor" in the run box.

---

### Post by colobix on 2010-02-22
ok i disabled it and restarted the pc but it's still there when I scroll over icons and stuff.
ANy other tips?

---

### Post by mcduck on 2010-02-22
> **tacantara said:**
> Here's a little trick you can try to get rid of those tooltips: Open a terminal (Applications-->Accessories-->Terminal) and enter **gconf**;  in it go to  "apps-->panel-->global" and almost at the bottom  there's an option called "tooltips_enabled". Just uncheck the box.

You can also access gconf by pressing ALT+F2, then enter gconf-editor in the box.  Press enter to run gconf, then follow the instructions above to navigate to the tooltips_enabled box.

That would only affect the panel, not the whole desktop.

---

### Post by colobix on 2010-02-22
Ok so is there any ways to solve this problem?

---

### Post by mcduck on 2010-02-22
> **colobix said:**
> Yes. It's the most annoying thing. I wish I could turn it off somehow.
That compiz this was too complicated. I understand the plugin part but after I have enabled the plugin, what do I do next?
And is that the only way to solve this problem?

Ok, here's a detailed explanation:

1. Install CompizConfig Settings manager (if you haven't got it already)

2. Use it to enable the "Opacity, Brightness and Saturation" -plugin

3. Go to that plugin's settings, to the Opacity-tab

4. Near the bottom of that dialog is a section called "Window specific settings". Click the "New"-button there.

5. Enter "type=tooltip" to the "windows"-field, and set the "Window values"-slider to zero.

6. Your tooltips just disappeared. :)

...and yes, this is the only way to hide tooltips everywhere on the Gnome desktop. Gnome's human interface guideline _requires_ programs to use tooltips, so there's no option to disable them. But this trick allows you to make them invisible.

---

### Post by colobix on 2010-02-22
Thank you SO much:)
It worked

---

