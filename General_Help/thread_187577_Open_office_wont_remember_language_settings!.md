---
title: "Open office wont remember language settings!"
date: 2006-06-03
forum: General Help
---

### Post by Morientes on 2006-06-03
My open office wont remember when I set its language to danish...everytime I restart it it is set back to some default (english(Australian) - which I dont even have instelled!).
What can I do?

---

### Post by Rui Pais on 2006-06-03
Hi,
Oo2 only remembers the language choice on a per-document basis.

Any 'New Document' will start as a default language that seems to be the same as the one of the interface! This is not annoying, is disasterous. Is a bug! 

Can someone suggest a solution or at least a work around?

(in my case i installed the Portuguese brazilian interface, now all my new docs became portuguese brazilian ignoring my dictionary of european portuguese. That's not even the same language. Not only vocabulary is different, but, most important, ortography **is** different. The suggestion for corrections from dictionary are plain wrong in my language... it's an anti-dictionary!)

---

### Post by grsing on 2006-06-03
I'm not on my Ubuntu computer now, but I know there is a way to change the OOo language for everything (or at least there was in 1.x, they might have changed something in 2.0, but it would be strange).  Look through those ridiculously huge options and preferences and all that and I think it's in there somewhere (I'll look when I'm back on the right computer and see if I can find it).

---

### Post by grsing on 2006-06-03
Not sure if OOo has the same menu structure on Linux as on Windows, but in the Windows version, it's Tools-Options-Language Settings-Languages, and change the "Default Languages for Documents", without checking the "For the current document only" box.  Let me know if that doesn't work (or if the menus are all different).

---

### Post by Rui Pais on 2006-06-04
hi, thanks for the reply.

No, thats the problem. If you have one document open you can change that set, and OO2 will remember your choice... for **that document**.

If you try to change "Default Languages for Documents" without any document open, to make it general, that option is greyed. It's not acessible :(


*EDIT:* btw, in both situations the option "For the Document Only" is always not acessible (greyed)

---

### Post by Morientes on 2006-06-04
No one knows how to change this? It is a little annoying!

---

### Post by Rui Pais on 2006-06-08
[QUOTE=Morientes]No one knows how to change this? It is a little annoying![/QUOTE]

a *little*... it has driving me mad :twisted:!!!


Here my [COLOR="Red"]***bad***[/COLOR] hack. (well it's not bad, only mean.)

Install the dictionay of your language and the openoffice.org-l10n-xx-XX package of your xx-XX language. This is optional. Works without it if you have the language dictionary installed.

Close any open session of OO.

```
cd /usr/lib/openoffice/share/registry/modules/org/openoffice/Setup/
sudo cp Langpack-en-US.xcu Langpack-xx-XX.xcu

```where <xx-XX> must be replaced for the language code.
In my case i have done for pt_BR -> pt_PT:
```
sudo cp Langpack-en-US.xcu Langpack-pt-PT.xcu 

```
now edit the new xcu:
```
sudo gedit Langpack-xx-XX.xcu
```
find and replace en-US for your xx-XX.

Launch Openoffice, and in Options | Languages put your language in every field, **including the 'User Interface'**, that is now "Available".
Restart Oo and as usual the documents will open in the language of 'User Interface'. 

If the language package is not installed, only the dictionary, Oo will have interface in en_US (Default) but documents will be in the "make-up" language. 

This is a bad hack but works here.

---

### Post by Morientes on 2006-06-08
Ok I might try this, but I find it very strange! I dont remember having the same problem in 5.10...or maybe I just can't remember! Weird though that one can't change the deault language! Definetly a bug!

---

### Post by zeca_pedra on 2006-07-06
Thanks for your help...it's an ugly hack but now I have the dictionary helping me in my native language - the portuguese from Portugal :-D

---

### Post by zeca_pedra on 2006-07-06
Sorry, in my last reply I didn't address quite well my thanks... they go for Rui Pais, of course ;-)

---

### Post by Rui Pais on 2006-07-07
hi zeca_pedra,
no problem (não há de quê ;))

it looks ugly but is harmless. 
Meanwhile i've been playing around with it and with the pt_BR package and make a small (amateur) pt_PT version from it. 
If you are interested you can check the a deb  [here]("http://homepage.oniduo.pt/rui.pais/linux/Openoffice.org-pt.zip").

Unfortunately, like everything related to Openoffice, is a mess. Translation packages aparently only contains translations of parts of the GUI not all OOo. So it replaces 'Arquivo' with 'Ficheiro', 'Exibir' with 'Ver' and so on but some Configuration windows and and Save confirmations will still have a 'Salvar' instead of 'Guardar'. I find it better then read brazilian eveywhere, anyway...

Have fun.

Até à "vista" :)

---

### Post by depi on 2006-08-25
I have this problem too!

It is a really bug, guys should fix them!!

---

### Post by ifokkema on 2006-08-26
Although I agree this looks like a bug, I believe a better way to fix this, is to save a template with the default language set to the preferred language, and use that template at all times.

---

### Post by peterroots on 2006-08-30
Not much help to you but I have been using openoffice.org2 using mandriva and it has been easy to change the default language - this is not so in kubuntu, even if you open all the configuration files for ooo, search and replace en-AU with en-GB (the language I wanted).  next time you open ooo the config files revert back to en-AU. grrr!

---

### Post by ifokkema on 2006-08-30
What if you do that to the system-wide files, located at /usr/lib/openoffice/share/ ?

---

### Post by florizs on 2006-09-04
Is this bug already reported? and to whom should this bug be reported?
I've been trying another workaround but it fails, it's getting annoying since I'm typing about 4 documents a day.

---

### Post by ifokkema on 2006-09-04
Hey, Leiden, daar werk ik :)

I think I found the bugreport (or related stuff) at:
[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/35936](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/35936)
[http://www.openoffice.org/issues/show_bug.cgi?id=65129](http://www.openoffice.org/issues/show_bug.cgi?id=65129)

---

### Post by nikosft on 2006-09-06
What I did was to chane the system defualt languafe from System->Administration->Language Support and the language for openoofice changed automatically

---

### Post by ifokkema on 2006-09-07
Interesting... but doesn't that change all your programs, terminal, Gnome stuff as well?

---

### Post by R U Bn on 2006-09-09
Guys,

I found it on [http://user-faq.openoffice.org/faq/ar01s05.html#id2874422](http://user-faq.openoffice.org/faq/ar01s05.html#id2874422).

Let me repeat what is relevant on that page for this thread.
Do it after selecting your whole document (CTRL-A on Windows).

> **My spellchecker does not seem to work ?**

Check your language settings for your document and whether a spellchecker is active for that language. Format|Character and the "Font" tab check "Language", there should be a tick mark beside the relevant language. 

Think this is the solution....

P.S. OpenOffice is just so annoying, just because they have another "way" of putting things.

---

### Post by ifokkema on 2006-09-11
> **R U Bn said:**
> P.S. OpenOffice is just so annoying, just because they have another "way" of putting things.
What if I said that Microsoft Office is annoying, because they have another "way" of putting things? Isn't that just the same?

[Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm").

See what I mean?

---

### Post by Speque on 2006-09-11
I changed the OpenOffice user interface language into finnish, and now it seems, that the default language for the documents also remains as finnish when I change it. You should try installing the correct UI-package for your language.

---

### Post by victorche on 2006-09-11
[http://www.openoffice.org/issues/show_bug.cgi?id=65129](http://www.openoffice.org/issues/show_bug.cgi?id=65129)
As you can see the bug is NOT in OpenOffice, but in the Ubuntu package...
I can confirm that there is not such a bug in OOo 2.0.3 on Slackware.

---

### Post by simohell on 2006-09-11
> **R U Bn said:**
> 
P.S. OpenOffice is just so annoying, just because they have another "way" of putting things.

I love the "way" OpenOffice does things. I've been using mainly StarOffice/OpenOffice since 5.0. OpenOffice is just so annoying, just because this thing has a Bug - changing default language used to work in Ubuntu 5.10 / OO.org2 v1.9x

---

### Post by peterroots on 2006-09-18
I have found the solution! I have posted it on the kubuntu forum at [http://kubuntuforums.net/forums/index.php?topic=6486.0](http://kubuntuforums.net/forums/index.php?topic=6486.0)
(read both by posts)

---

### Post by ifokkema on 2006-09-18
Nice... I guess for us Ubuntu users that's at System -> Administration -> Language Support...

---

### Post by simohell on 2006-09-28
> **peterroots said:**
> I have found the solution!

I'm sorry but I don't get your solution. For the bug in OpenOffice.org2 Ubuntu version it is not solution is not to change ones operating system to another language.

I myself cannot really work if I set my operating system and aplications to the language I need for OpenOffice.org2 to be the default language. What I need is an option to set a different default language for the spellchecking and hyphenation than what I have in the user interface.

---

### Post by simohell on 2006-09-28
> **ifokkema said:**
> Although I agree this looks like a bug, I believe a better way to fix this, is to save a template with the default language set to the preferred language, and use that template at all times.

A template is a quite good solution for this problem. I just had to figure out how to set the default template. So now I don't need to select the template manually, and it functions just as it would with my native language being the OOo2 default.

So HOWTO:

1. Change the language for the current document

Tools -> Options -> Language Settings -> Languages -> Default languages for documents

2. Save it as a template (best place is ~/.openoffice.org2/user/template)

3. Go to File -> Templates -> Organise

4. Choose your template from "My Templates" (the folder .../user/template) an choose Command -> Set As Default Tempalte

5. Do the same thing with a spreadsheet template with the desired language


Wheee! Im happy again for the first time after upgrading to Dapper ;)

---

### Post by RikoW on 2006-09-29
I had the same problem with the language settings as reported above. In the end, I threw out the ubuntu OOo version and installed the lastest OOo from [www.openoffice.org](www.openoffice.org) via alien + dpkg. There are threads in this forum, which explain how to do that.

No problem with language settings there, just use:



Tools -> Options -> Language Settings -> Languages to switch


Cheers,
               Riko

---

### Post by ifokkema on 2006-09-29
> **RikoW said:**
> No problem with language settings there
Yes, it's a known bug in the Ubuntu release, as other distro's don't have this problem either.

---

### Post by Oki on 2006-11-01
So the problem is not with OpenOffice, but with Ubuntus version of it. Do we know if the Ubuntu team is working on it? This thread is 4 weeks old, and I still have this problem](*,) ...

---

