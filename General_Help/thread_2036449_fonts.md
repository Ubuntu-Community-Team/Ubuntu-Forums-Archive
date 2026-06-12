---
title: "fonts"
date: 2012-08-01
forum: General Help
---

### Post by pjmlmas on 2012-08-01
If I were wanting to download a font, New Century Schoolbook, what steps to take, if possible?

Then, how to have OpenOffice use these fonts?

---

### Post by GreatDanton on 2012-08-01
1.Download the font you would like to have.
2. Extract it somewhere
3. In terminal type: ```
gksudo open nautilus
```
4.(now you have two nautilus opened) copy&paste extracted files into .fonts folder
Destination is /home/username/.fonts  . It's hidden folder so you will have to make it visible (ctrl+h if I remembered correct)

5. After you copied the stuff in there, open terminal again.
```
 fc-cache -fv
```

6.Done

Hope this helps.

Regards.

---

### Post by pjmlmas on 2012-08-02
Not really. I am reading online that my system should have this font. Is this a standard font?
Can it be used with OpenOffice?

---

### Post by kostkon on 2012-08-03
> **pjmlmas said:**
> Not really. I am reading online that my system should have this font. Is this a standard font?
Can it be used with OpenOffice?
New Century Schoolbook [is not a free font]("http://www.myfonts.com/fonts/linotype/new-century-schoolbook/").

It comes with MS Word though, so let's say an average Windows system usually will have this font already, yes. So, maybe if you have a copy of Word lying around you could try getting the font(s) from there.

You don't need to follow the complicated instructions that GreatDanton has given you, though; just double click on the font file and press the Install Font button.

---

### Post by clbph on 2012-09-20
> **GreatDanton said:**
> 1.Download the font you would like to have.
2. Extract it somewhere
3. In terminal type: ```
gksudo open nautilus
```4.(now you have two nautilus opened) copy&paste extracted files into .fonts folder
Destination is /home/username/.fonts  . It's hidden folder so you will have to make it visible (ctrl+h if I remembered correct)

5. After you copied the stuff in there, open terminal again.
```
 fc-cache -fv
```6.Done

Hope this helps.

Regards.

OK, this is getting me where I want to go. Step 1 to 3 works fine. Not sure by what you mean by "two nautilus opened", but I do have browser window opened and my original terminal window is still open. Yes, ctrl+h shows the hidden folders, but things break down at this point. I have a home folder, no problem there, but I am not seeing a folder with my name on it (or one with username).

In the home folder are:
     Desktop
     .cache
     .config
     .dbus
     .gnome2
     .pulse
          .bashrc
          .profile
          .pukes-cookies

based on the iconography, the last three look like data files and do not open. I've tried exploring the other folders, but do not see a ".fonts" folder.

What am I missing here? I'm aboput to leave for the day, but I'll be checking tomorrow.

Thanks for the help to this point!

---

### Post by oldos2er on 2012-09-20
> **clbph said:**
>  I've tried exploring the other folders, but do not see a ".fonts" folder.

I don't think it's there by default, but it's easily created: ```
mkdir .fonts
``` You don't need or want to use "gksudo" or "sudo" inside your home folder.

---

