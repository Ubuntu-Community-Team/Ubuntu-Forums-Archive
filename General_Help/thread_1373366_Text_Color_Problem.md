---
title: "Text Color Problem"
date: 2010-01-05
forum: General Help
---

### Post by IAmCorbin on 2010-01-05
I have an annoying text color problem. I don't know what to change to fix it. I have played around with System->Preferences->Appearance to no avail.

Here is the problem:
[IMG]http://www.iamcorbin.net/Screenshot-FileZilla.png[/IMG]

I am getting very light colored text so only the currently selected item is readable. The funny thing is that in Nautilus, Firefox, Chrome, Amarok, etc.. it's fine. It seems to be in only some programs in boxes with selectable line items, but also in the area that displays status updates in FileZilla. So I'm not sure how to pinpoint the problem.

Help Please.

Thanks,
~Corbin

---

### Post by stinkeye on 2010-01-05
Try gnome-color-chooser

---

### Post by IAmCorbin on 2010-01-05
I can't seem to get anywhere with gnome-color-chooser either. I have everything set to dark colors and nothing is changing the desired colors:

[IMG]http://www.iamcorbin.net/Screenshot.png[/IMG]

---

### Post by stinkeye on 2010-01-05
I'll install filezilla and have a look. What theme are you using?

---

### Post by Strongman332 on 2010-01-05
I don't know if you tried this change your theme to the defualt

---

### Post by stinkeye on 2010-01-05
Yes , I  would change to a different theme where the default text in the window is dark.

---

### Post by stinkeye on 2010-01-06
> **samshana said:**
> Ok this is now bleeding into the Shop Home page also, any ideas I'm really at a loss here, even trying to change the color via the text editor for the page doesn't stay put. I've double checked my Theme to make sure it's still all intact text wise and nothing's changed it's all supposed to be the purple text not the black at all.

*EDIT* I was able to get the text to change to the purple in the editor of the Shop Home Page, I don't know if it's going to stay or not, but it should already be showing up purple not black due to the settings in the Theme I thought? This just started yesterday to do this, I haven't changed anything on this theme, I've worked on a Xmas one this week but that is basically the same thing with different graphics on it so it should be all good and shouldn't have changed anything like this I wouldn't think?

I'm pretty baffled here, it's probably something really stupid and obvious and I just can't see it as usual lol. I sure hope someone has an idea what's wrong because I really don't want to have to edit all my products that start doing this after I've added them
====================

Has this got anything to do with the what the OP is talking about?
No idea what your trying to say.

---

### Post by Yellow Pasque on 2010-01-06
> **stinkeye said:**
> Has this got anything to do with the what the OP is talking about?
No idea what your trying to say.
It's a spambot and I've reported it.

---

### Post by IAmCorbin on 2010-01-06
> **Strongman332 said:**
> I don't know if you tried this change your theme to the defualt

I have tried every theme in System->Preferences->Appearence

---

### Post by stinkeye on 2010-01-06
This is what it looks like for me running the human theme.
I also can't change the color of the window or text no matter 
what theme I use, so I can't work out why yours is different.

[COLOR="DarkRed"]**_Edit:_**[/COLOR]The window and text colors do change when I restart filezilla.
One thing I did do was go into the filezilla settings and have a look at the different themes but put it back
on the Open crystal theme and clicked the ok button.
Maybe this created a setting in the ~/.filezilla folder.
You can also try renaming your ~/.filezilla folder to ~/.filezilla.bak  and it will create a new folder when you start filezilla.

---

### Post by IAmCorbin on 2010-01-06
> **stinkeye said:**
> This is what it looks like for me running the human theme.
I also can't change the color of the window or text no matter 
what theme I use, so I can't work out why yours is different.

[COLOR=DarkRed]**_Edit:_**[/COLOR]The window and text colors do change when I restart filezilla.
One thing I did do was go into the filezilla settings and have a look at the different themes but put it back
on the Open crystal theme and clicked the ok button.
Maybe this created a setting in the ~/.filezilla folder.
You can also try renaming your ~/.filezilla folder to ~/.filezilla.bak  and it will create a new folder when you start filezilla.

The FileZilla themes change the icons but not the colors.

The problem isn't only in FileZilla though, Code::Blocks IDE is doing the same thing, and I'm pretty sure I've had it come up in another application as well, but I can't remember which one. The only color I can seem to affect with gnome-color-chooser is** Entry fields** alt. selected which changes the selection back color when the application does not have focus. 

Where else in gnome could these colors be getting set?

---

### Post by stinkeye on 2010-01-06
The only other place I know is Appearence > customize > colors or
in ~/.gtkrc-2.0

---

### Post by IAmCorbin on 2010-01-06
> **stinkeye said:**
> The only other place I know is Appearence > customize > colors or
in ~/.gtkrc-2.0

I don't have a ~/.gtkrc-2.0 folder

---

### Post by IAmCorbin on 2010-01-06
Doh!! ::smacks forehead:: 

I'm an idiot. I didn't try closing FileZilla after changing my theme. FileZilla and Code::Blocks IDE just don't display correctly in the Dark Room theme. If I change the theme and *then* open FileZilla it works fine.

Oops.

Thanks for the help anyways,
~Corbin

---

### Post by stinkeye on 2010-01-06
Haha, its always something simple.
It's like when you loose something and search in ever widening circles
and then find it back where you started.

---

