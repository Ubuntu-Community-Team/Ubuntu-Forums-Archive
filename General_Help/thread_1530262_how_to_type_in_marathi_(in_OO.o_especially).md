---
title: "how to type in marathi (in OO.o especially)?"
date: 2010-07-13
forum: General Help
---

### Post by nightshade209 on 2010-07-13
I am using Ubuntu 10.04. My dad wants to type in Marathi. I found the necessary fonts [[COLOR="Blue"]_here_[/COLOR]]("http://www.angelfire.com/pop/top4/fonts/marathi.zip"), but simply unzipping them and putting them in the ".fonts" folder under /home/user does not help, as whenever I select the font, it still keeps typing in English. I have also installed the necessary packages from System>Administration>Language Support, but I do not know what difference that has made.
Also, googling it turns up results for Hindi, and since Hindi and Marathi have some differences in vowels, that does not seem to work. 
I also got a few other .ttf files for the script as such, but each seems to have its own, distinct layout. What I need is a standardized one. Any help?
P.S.: My dad is reluctant to go through any complicated procedures everytime he wants to type, so a simple solution would be greatly appreciated.

---

### Post by nightshade209 on 2010-07-18
ok, found the answer. Had to install a couple of fonts and tools, including the language from keyboard layout.

---

### Post by simosx on 2010-07-20
It would help to describe what you did to solve the problem.
This would help others but most importantly it would help to pinpoint ways to enhance what you did to solve the problem.

The proper way this should work is if by selecting just Marathi in the Language Support, all should work. You would need to logout, select Marathi and login again. Anything less than that means that there is work yet to do.

---

### Post by nightshade209 on 2010-07-21
Ok, here's how I did it, as far as I remember:
1. Run 
```
sudo apt-get install ttf-marathi-fonts
```
2. Right-click on the GNOME-panel, select "Add to Panel" > Keyboard Accessibility Status.
3. Right-click on the button, select Preferences > Layout tab
4. Click "Add". Select "India Hindi Wx" from the dropdown menu. A small button showing your default keyboard layout appears in the Notification Area. (For me, it read USA.)
5. Whenever you wish to type in Marathi, right-click on the layout button > Groups > India Hindi Wx (You can cycle through the installed layouts by left-clicking it.)
6. In the program you are using (OO.o Writer in my case), select Lohit Marathi as the font, and type away.

Note: This will presumably work for any language supported in the Keyboard Layout list.
Also, even if you do not install any font and merely switch the layout, you will be able to type in Marathi; however, not all vowels, consonants and letter-combinations (especially "pra", "kra" and other combinations like that) will be displayed properly. Lohit Marathi displays all of them properly.
Once the layout button is displayed in your Notification Area, you can delete the Keyboard Accessibility Status button you added in step 2.

---

### Post by simosx on 2010-07-21
> **nightshade209 said:**
> Ok, here's how I did it, as far as I remember:
1. Run 
```
sudo apt-get install ttf-marathi-fonts
```
2. Right-click on the GNOME-panel, select "Add to Panel" > Keyboard Accessibility Status.
3. Right-click on the button, select Preferences > Layout tab
4. Click "Add". Select "India Hindi Wx" from the dropdown menu. A small button showing your default keyboard layout appears in the Notification Area. (For me, it read USA.)
5. Whenever you wish to type in Marathi, right-click on the layout button > Groups > India Hindi Wx (You can cycle through the installed layouts by left-clicking it.)
6. In the program you are using (OO.o Writer in my case), select Lohit Marathi as the font, and type away.

Note: This will presumably work for any language supported in the Keyboard Layout list.
Also, even if you do not install any font and merely switch the layout, you will be able to type in Marathi; however, not all vowels, consonants and letter-combinations (especially "pra", "kra" and other combinations like that) will be displayed properly. Lohit Marathi displays all of them properly.
Once the layout button is displayed in your Notification Area, you can delete the Keyboard Accessibility Status button you added in step 2.

Thanks for your report.

1. If you have the chance to configure a new Ubuntu 10.04 system with Marathi, try with System»Preferences»Language Support, and select Marathi from the list. This should install the required fonts, namely 'ttf-marathi-fonts'. In addition it should install any available translations and you will have the option to have Ubuntu in Marathi.

2. To try out the Marathi Ubuntu, you need to logout and at the login screen select the Marathi language. Then login. You can change back at any time you want.
The Marathi translation is quite good; see some stats at [http://l10n.gnome.org/teams/mr](http://l10n.gnome.org/teams/mr)

3. You are using the basic keyboard layout support in Ubuntu for Marathi. This is fine. Since you can write Marathi well, this is OK. The 'basic keyboard layout support' (accessible through Keyboard Preferences) is pre-installed in Ubuntu, so it can be used even without adding the language support.

4. It's important to add the language support to the best of the fonts. Ubuntu probably comes with a generic Devanagari font that does not cover Marathi. So, if you install and use the Marathi language setting, Ubuntu will know that you want Marathi and will use the Marathi characters from the Marathi font. There is a chance that some of the common characters with Devanagari will come from the generic Devanagari font.

5. When you type in Openoffice and Marathi, the system should be able to show Marathi even if the selected font is 'Sans' due to font substitution. A nice trick here is to change the document styles so that 'Default', 'Text body', 'Heading 1', 'Heading 2' have the Marathi font by default. Then save these as the default settings for OpenOffice.

---

### Post by nightshade209 on 2010-07-21
Ok, thanx! Will keep it in mind if I ever have to configure the whole system in Marathi; but for now, I just need it in documents.
Appreciate the tips... :)

---

### Post by rahul_bhise on 2010-12-03
> **nightshade209 said:**
> Ok, here's how I did it, as far as I remember:
1. Run 
```
sudo apt-get install ttf-marathi-fonts
```
2. Right-click on the GNOME-panel, select "Add to Panel" > Keyboard Accessibility Status.
3. Right-click on the button, select Preferences > Layout tab
4. Click "Add". Select "India Hindi Wx" from the dropdown menu. A small button showing your default keyboard layout appears in the Notification Area. (For me, it read USA.)
5. Whenever you wish to type in Marathi, right-click on the layout button > Groups > India Hindi Wx (You can cycle through the installed layouts by left-clicking it.)
6. In the program you are using (OO.o Writer in my case), select Lohit Marathi as the font, and type away.

Note: This will presumably work for any language supported in the Keyboard Layout list.
Also, even if you do not install any font and merely switch the layout, you will be able to type in Marathi; however, not all vowels, consonants and letter-combinations (especially "pra", "kra" and other combinations like that) will be displayed properly. Lohit Marathi displays all of them properly.
Once the layout button is displayed in your Notification Area, you can delete the Keyboard Accessibility Status button you added in step 2.

thanks i to was searching for the same.
your post helped me a lot

---

