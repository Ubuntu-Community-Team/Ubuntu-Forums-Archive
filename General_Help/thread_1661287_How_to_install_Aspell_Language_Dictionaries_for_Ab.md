---
title: "How to install Aspell Language Dictionaries for Abiword in Ubuntu 10.10"
date: 2011-01-06
forum: General Help
---

### Post by Merlin2007 on 2011-01-06
[FONT=Fixedsys]:confused:I searched the web on how to install another language dictionary for Abiword, all I got was cryptic instructions that where way too geeky to follow, extract this, make file this blah blah blah. I don't understand this silly mentality of developers....please make it simple, you do not need to have a computer degree to do this!!! 

Luckily Ubuntu is making things easier. So here I'm sharing an easy way to do it just using Ubuntu Software Centre. The key here is knowing what to type in the search box.

After you have installed the dictionaries that you need,  just Start Abiword, go to **Tools > Set Language... > Choose the language that you want to use for the session**. 


_**Method One** (fastest method)_
Start Ubuntu Software Centre....Go to **Applications > Ubuntu Software Centre**, in the search box type **gnu aspell**. All dictionaries should be listed.
Select the dictionary you need, and click install. How easy can it get!!!:p

_**Note:**_ [I]This needs to be fixed, since when I searched for **aspell** in Ubuntu Software Centre nothing comes up....not even a hint pointing me to the right direction, instead it assumes that you know the correct name for the application....**gnu aspell**. 
[/I]

_**Method Two** (longer but I discovered some other errors that need to be fixed)_
Start Ubuntu Software Centre....Go to **Applications > Ubuntu Software Centre**, in the **search box** type the name for the dictionary you need.
Here is an alphabetical list of all available dictionaries for **GNU Aspell** and what you need to search for in Ubuntu Software Centre.

_**Dictionary**_                      _**Search for**_

**A**
Africaans dictionary **     aspell-af**
Amharic dictionary        **aspell-am**
Arabic dictionary **          aspell-ar**
Arabic Large dictionary  **aspell-ar-large**
Armenian dictionary **      aspell-hy**

**B**
Basque (Euskera) dictionary ** aspell-eu-es**
Bengali dictionary                **aspell-bn**
Bulgarian dictionary **            aspell-bg**
Breton dictionary **                 aspell-br**

**C**
Catalan dictionary **     aspell-ca**
Croatian dictionary **    aspell-hr        **
Czech dictionary **        aspell-cs**

**D**
Danish Comprehensive dictionary **aspell-da**
Dutch dictionary **                         aspell-nl**
     
**E**
English dictionary        **aspell-en**
Esperanto dictionary **   aspell-eo**
Estonian dictionary **     aspell-et **

**F**
Faroese dictionary       **aspell-fo**
Finnish dictionary        **aspell-fi**
French dictionary **        aspell-fr**

**G**
German dictionary                      **aspell-de**
German dictionary (old spelling)  **aspell-de-alt**
Greek dictionary **                        aspell-el**
Gujarati dictionary                      **aspell-gu**

**H**
Hebrew dictionary **       aspell-he**
Hindi dictionary **          aspell-hi**
Hungarian dictionary    **aspell-hu**

**I**
Icelandic dictionary **         aspell-is**
Irish (Gaeilge) dictionary  **aspell-ga**
Italian dictionary **             aspell-it**

**J**

**K**
Kurdish dictionary **          aspell-ku**

**L**
Latvian dictionary **           aspell-lv**
Lithuanian dictionary       **aspell-it**

**M**
Malayalam dictionary **    aspell-ml**
Marathi dictionary          **aspell-mr**

**N**
Ndebele dictionary **      aspell-nr**
Norwegian dictionary    **aspell-no**

**O**
Oriya dictionary           **aspell-or**

**P**            
Portuguese dictionaries **                aspell-pt**
Portuguese Brazilian dictionary      **aspell-pt-br**
Portuguese European dictionary     **aspell-pt-pt**
Persian dictionary **                        aspell-fa**
Polish dictionary **                          aspell-pl**
Punjabi dictionary **                        aspell-pa**

**Q**

**R**
Romanian dictionary **    aspell-ro**
Russian dictionary **       aspell-ru**

**S**
Slovak dictionary **              aspell-sk**
Slovenian dictionary **          aspell-sl**
Sorbian Upper dictionary    **aspell-hsb**
Sotho Northern dictionary **  aspell-ns**
Sotho Southern dictionary **  aspell-st**
Spanish dictionary              **aspell-es**
Swazi dictionary **                aspell-ss**
Swedish dictionary [B]            aspell-sv
[/B] 
**T**
Tagalog dictionary **             aspell-tl**
Tamil dictionary **                 aspell-ta**
Telugu dictionary                **aspell-te**
Tsonga dictionary                **aspel-ts**
Tswana dictionary **              aspel-tn**

**U**
Ukranian dictionary **            aspell-uk**
Uzbeck dictionary                **aspell-uz**

**V**

**W**
Welsh dictionary **                 aspell-cy**

**X**
Xhosa dictionary **                 aspell-xh**

**Y**

**Z**
Zulu dictionary **                   aspell-zu**


_**Note:**_  *The Italian dictionary (**aspell-it**) the Oriya dictionary (**aspell-or**) and the German dictionary (**aspell-de**) do not show up correctly in Ubuntu Software Centre when you individually search for them.*

[I]For the German dictionary **aspell-de** the solution is to search **aspell-de-alt** and Ubuntu Software Centre will show you **aspell-de** where you can install it.
[/I]
For the Italian and Oriya dictionaries you will need to either use **method one** or use Synaptic Package Manager instead to install those dictionaries until this is fixed.

To Use Synaptic Package Manager Go to...
**System > Administration > Synaptic Package Manager**. Type your password, in search type the above dictionaries, click on the box to put an x, hit the apply button.

If you want to install Aspell documentation search for** aspell-doc** in Ubuntu Software Centre. The documentation is web page based, therefore start Firefox and in the address bar copy and paste the following to see it. 
**file:///usr/share/doc/aspell-doc/aspell.html/index.html**

In case you were not aware All Programs documentation is placed in the user (usr) share directory under the Doc folder.
[U][B]
Note:[/B][/U] *Again there is a problem here that needs to be fixed, Ubuntu Software Centre should tell you where the documentation will be installed, yet it doesn't.*

**_What is Aspell?_**
GNU Aspell is a spell checker designed to eventually replace Ispell. It can either be used as a library or as an independent spell checker. Its main feature is that it does a much better job of suggesting possible replacements for a misspelled word than just about any other spell checker out there for the English language. Unlike Ispell, Aspell can also easily check documents in UTF-8 without having to use a special dictionary. Aspell will also do its best to respect the current locale setting. Other advantages over Ispell include support for using multiple dictionaries at once and intelligently handling personal dictionaries when more than one Aspell process is open at once. 

Hope you found this helpful!!):P


[/FONT]

---

### Post by spielball on 2011-12-23
Thanks a lot. I was looking for that info. Now I have my German spellcheck dictionary in AbiWord. I just typed "German aspell" in the search box of the software center.

---

