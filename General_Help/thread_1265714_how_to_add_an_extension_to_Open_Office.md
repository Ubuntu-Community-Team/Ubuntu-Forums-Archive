---
title: "how to add an extension to Open Office"
date: 2009-09-13
forum: General Help
---

### Post by rahrahmah on 2009-09-13
This is going to seem like a stupid question, but I'm trying to add a Canadian English dictionary to Open Office because my spell check isn't working. When I click on the extension to add it, a box pops up asking me "where" to add it. I don't know where open office is. I can't find any of my program files. Obviously there are choices, but the place where I would think they'd be, File System doesn't have anything that looks related to my programs. The open office tutorials are not for linux and are no help. Thanks in advance.

---

### Post by DenysT on 2009-09-14
Easiest way is to use Tools -> Language -> More Dictionaries Online... option. This will open a Firefox (or whatever browser you are using) window with all the available dictionaries. Select the dictionary you want and save the file to your desktop or home folder. Next use Tools -> Extension Manager to add the saved file. Click the Add... button and navigate to where you saved the .oxt file and select it.

I usually do this inside of Writer.

---

### Post by rahrahmah on 2009-09-14
See, it's the last part of your instructions that's tripping me up. I don't know where it's saved. I don't know where to navigate to after I click add. I don't know where the files for open office are.

---

### Post by DenysT on 2009-09-14
> **rahrahmah said:**
> See, it's the last part of your instructions that's tripping me up. I don't know where it's saved. I don't know where to navigate to after I click add. I don't know where the files for open office are.

By default Firefox saves to the desktop. Look for the file there first. If you don't see it go to Edit -> Preferences Main tab in Firefox to find out where it is saving the file. The file should be named **en_CA_2_0_0.oxt **for the dictionary you want.

Then with OpenOffice Writer opened to a blank or existing document just use the extension manager I mentioned earlier to add the dictionary by navigating to the folder where the file is saved. It's not the where OpenOffice files are located but where the extension file is located.

---

### Post by rahrahmah on 2009-09-15
My firefox DOES save to the desktop. There is no package on my desktop. I searched all my files and it says that "**en_CA_2_0_0.oxt" **doesn't exist. And you're right, that's the dictionary I want. Should it be a package on the desktop before I can go to "add" in the extension manager?

What I did was I went to the website, I got the little package, then when I go to the extension manager it's listed, and so I click "add" it wants to know where to add it. I don't know where to add it to. I tried adding it to the desktop but it makes me want to choose a folder. It won't let me add it to just the desktop.

---

### Post by rahrahmah on 2009-09-16
Please, I can't spell check anything. It won't work, and as far as I can tell, this is the only way I can fix it. I can go into the internet to spell check, but it's a hassle. I'm in university again for the first time in years. I want to do well, not submit things full of spelling and grammar errors.

---

### Post by DenysT on 2009-09-16
> **rahrahmah said:**
> My firefox DOES save to the desktop. There is no package on my desktop. I searched all my files and it says that "**en_CA_2_0_0.oxt" **doesn't exist. And you're right, that's the dictionary I want. Should it be a package on the desktop before I can go to "add" in the extension manager?

What I did was I went to the website, I got the little package, then when I go to the extension manager it's listed, and so I click "add" it wants to know where to add it. I don't know where to add it to. I tried adding it to the desktop but it makes me want to choose a folder. It won't let me add it to just the desktop.

If it's listed in the extension manager it is in OpenOffice. All you need to do is activate it. If you select it in extension manager it should have a Disable and Remove button (or an Enable if it's not enabled). If its not enabled then click the Enable button. Under the Tools -> Options menu dialog box go to the Language Settings -> Languages tree panel. Look for the Default languages for documents Western drop down list and scroll to English (Canada) and select it. Click OK.

Also on the bottom status bar is a panel that has the current default language selected for the document. When you click on that panel you have the option of selecting More... which will bring up a Font dialog box with a drop down list like above for changing the language used for spell checking the document.

---

### Post by rahrahmah on 2009-09-16
Ok, this all looks like it's in order... So I'm still confused then. Why won't my spell-check work? It doesn't matter what the mistake is, from confusing their and thier or just going alsdkjfdejkf it won't pick up the errors...

---

### Post by DenysT on 2009-09-17
> **rahrahmah said:**
> Ok, this all looks like it's in order... So I'm still confused then. Why won't my spell-check work? It doesn't matter what the mistake is, from confusing their and thier or just going alsdkjfdejkf it won't pick up the errors...

Are you doing a manual spell check from the toolbar or menu? Or are you wanting OpenOffice to check as you type? If it is the latter make sure you have the option turned on in Options -> Language Settings -> Writing Aids. Its the first option listed under the Options select box. Also to correct their from thier make sure you have autocorrect turned on, Format -> AutoCorrect -> While Typing should have a check mark next to it. It might be worthwhile to check out what option Autocorrect is using after selecting Autocorrect.

---

### Post by houseworkshy on 2010-02-12
deleted

---

### Post by fisheater on 2010-02-12
I had the same problem, check this for a nice fix: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=67](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=67).

My question for the forum is how to get two dictionaries working at the same time? I have CDN english + OpenMedSpel (en-us) installed but it still is not catching many spelling errors.

TY

FE

---

### Post by Hagar Delest on 2010-02-13
> **fisheater said:**
> My question for the forum is how to get two dictionaries working at the same time? I have CDN english + OpenMedSpel (en-us) installed but it still is not catching many spelling errors.
This should be feasible if that dictionary follows the same rules than the OOo ones. In this case, you just have to tweak the files described in the tutorial. Is this dic made of .dic and .aff files?

---

### Post by fisheater on 2010-02-14
> **Hagar de l'Est said:**
> This should be feasible if that dictionary follows the same rules than the OOo ones. In this case, you just have to tweak the files described in the tutorial. Is this dic made of .dic and .aff files?

Hagar,

Always there to save the OOo day. I will have a closer look at the tutorial and see. After a quick review of your tutorial, I am afraid I don't understand your question. I admit that this problem is 99.9% related to my lack of understanding on how to use/activate the dictionary.

I used the dictionaries and add-ons in the pic.

[[IMG]http://img716.imageshack.us/img716/4167/ooodict.png[/IMG]](http://img716.imageshack.us/i/ooodict.png/)

TY

FE

---

### Post by Hagar Delest on 2010-02-14
I've tried it yesterday and it works (note that I've had troubles first because I had kept my user profile for a long time so I've had to reset it).

1. Disable the OpenMed extension. Then, close OOo completely.
2. Go to the extension folder in your user profile (see tutorial)
3. Edit the Dictionaries.xcu file and instead of [FONT="Courier New"]<en-US>[/FONT] string, put [FONT="Courier New"]<en-US en-CA>[/FONT] (CA is for Canadian entry, IIRC).
4. Relaunch OOo and enable the extension.
The OpenMed dic should work in parallel with the standard one.

---

### Post by rimshot4 on 2010-05-18
> **Hagar de l'Est said:**
> I've tried it yesterday and it works (note that I've had troubles first because I had kept my user profile for a long time so I've had to reset it).

1. Disable the OpenMed extension. Then, close OOo completely.
2. Go to the extension folder in your user profile (see tutorial)
3. Edit the Dictionaries.xcu file and instead of [FONT="Courier New"]<en-US>[/FONT] string, put [FONT="Courier New"]<en-US en-CA>[/FONT] (CA is for Canadian entry, IIRC).
4. Relaunch OOo and enable the extension.
The OpenMed dic should work in parallel with the standard one.

Hagar, 

I've been working on this problem FOREVER with OpenMedSpel! I didn't get the script edit to work, but I simply enabled the Canadian English option under Tools-->Language-->All Text. Now my default Canadian English and American Medical English spellcheck work just fine, side by side. I'm fine as long as they don't spell differently up there now, eh? 

Thanks so much!

---

### Post by Hagar Delest on 2010-05-18
Strange because the Tools>Lanuguage>... dialog is just a direct formatting that overrides the paragraph and character styles. So there is no big difference with the other users experience.

But perhaps they have changed the extension settings in the meantime.

---

