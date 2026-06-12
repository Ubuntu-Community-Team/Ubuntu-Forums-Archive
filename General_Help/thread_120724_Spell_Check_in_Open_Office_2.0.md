---
title: "Spell Check in Open Office 2.0"
date: 2006-01-23
forum: General Help
---

### Post by ubuntu27 on 2006-01-23
[QUOTE=johnnymo87]Hmmm, I'm getting permission problems. When running the apt-get, I get this:
[i]
jcm05003@zenith:~$ apt-get install myspell-en-us
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
[/i]
With synaptic I get:
[i]
Failed to run /usr/sbin/synaptic as user root:
 Wrong password.
[/i]
I have installed many applications both through the command line and synaptic before. Any ideas on how to solve this new problem?

Edit: I went into root mode, and got it to work. Why did I have to do this? I never had to do it that way before.[/QUOTE]

You forgot to use "sudo" 

sudo apt-get install myspell-en-us

and then type your password. And done! :D  ;)

---

### Post by johnnymo87 on 2006-01-23
I cannot get spell check to work in open office. It does not pick up on any misspelled words. I have to hand a paper in in one hour! Does anyone know how to get this to work?

I'm guessing it has something to do with there not being a dictionary already preloaded into open office.

Edit: Also, I have a HP Deskjet 540 printer, which won't print from my computer. What do I need to do to get the computer to recognize it and print from it?

---

### Post by dpm on 2006-01-23
Try to install myspell from the repositories, either with synaptic or from the command line:
[B]
sudo apt-get install myspell-en-us[/B]

(assuming you need spell checking for US English, otherwise install the myspell dictionary of the language you need).

Then in OpenOfice you can go to Tools>Options>Language Settings>Writing Aids>Available Language Modules>Edit... and there you can see the different dictionaries you've got installed.

Hope it helps.

Edit: as someone pointed out, I had forgotten to add sudo to the command...

---

### Post by dcstar on 2006-01-23
[QUOTE=desp]Try to install myspell from the repositories, either with synaptic or from the command line:

apt-get install myspell-en-us

(assuming you need spell checking for US English, otherwise install the myspell dictionary of the language you need).

Then in OpenOffice you can go to Tools>Options>Language Settings>Writing Aids>Available Language Modules>Edit... and there you can see the different dictionaries you've got installed.

Hope it helps.[/QUOTE]
And you also have to ensure that the Spelling Language you have installed is valid/set for the document language you are using!

If you get this wrong, OO won't check the document....     :(

---

### Post by johnnymo87 on 2006-01-23
Hmmm, I'm getting permission problems. When running the apt-get, I get this:
[i]
jcm05003@zenith:~$ apt-get install myspell-en-us
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
[/i]
With synaptic I get:
[i]
Failed to run /usr/sbin/synaptic as user root:
 Wrong password.
[/i]
I have installed many applications both through the command line and synaptic before. Any ideas on how to solve this new problem?

Edit: I went into root mode, and got it to work. Why did I have to do this? I never had to do it that way before.

---

### Post by Elena678 on 2007-01-06
What file dus i need to install to have a icelandic spell corection?

can i just use package manager to install it, or do i need to fix it in a difficlude way like te people did here in this thread before, i alreasy have the swedish spell check, so spell check is allready installed.

thanks a lot ;)

greetings

---

### Post by Hagar Delest on 2007-01-06
You can see here for detailed information : [[Tutorial] Spell check]("http://www.oooforum.org/forum/viewtopic.phtml?t=50862").

---

### Post by Elena678 on 2007-01-06
Thank you

---

### Post by domer on 2007-04-07
Easy fix to this problem is: 

1. Start Open Office (i am using OO 2.0)
2. Tools -> Options -> Expand "Language Settings" -> Double click on "Languages"
3. Under the "Language of" section change "Locale setting" to [COLOR="Blue"]**English(USA)**[/COLOR]
4. Under the "Default language for documents" select [COLOR="Blue"]**English(USA)**[/COLOR] as Western Languages

You can also chose English (UK). Open Office provides spell check only for USA and UK English. Changing "Locale setting" is important unless you want to change the default language document to English (USA/UK) everytime you want spell check. 

Hope this helps. I have seen posts which suggest installing dictionary packages. Haven't ventured myself, so can't comment.

---

### Post by joao82 on 2008-04-12
I did this for portuguese:

sudo apt-get install myspell-pt-pt

and it worked like a charm
this thread was helpful, thanks

---

