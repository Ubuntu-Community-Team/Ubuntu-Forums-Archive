---
title: "Libra office invoice"
date: 2011-06-22
forum: General Help
---

### Post by maz32 on 2011-06-22
So my story goes that im doing a old neighbor a favor by computerizing his business (just himself and technically me now)
so i have made/ making him a website with google sites  and im organizing him a computer because he doesn't have one. so i re formated a old xp machine his family used and put xubuntu on it sadly this ~2002 is struggling so we have planed on buying a cheap i3 system and put on ubuntu on it straight off.
Now the important bit

i said to him that i could probably make him something for him to put his invoices on and his only real request was that if he could have a constant invoice number appear.
so i had a look about a month ago and their wasn't much in terms of help only some OOo stuff that didn't work. Recently i found this [http://dag.wieers.com/blog/libreoffice-creating-invoices-using-writer](http://dag.wieers.com/blog/libreoffice-creating-invoices-using-writer) but im having trouble with it.

so the question is 
could someone explane in full detail what to do or
make a tutorial 
could point me to somewhere else that has help on the above
something differnt eg. software (with simple documentation) or database
or make a  new plane English noob friendly one?

   
i know this is a big ask but i would thank anyone very much and if you wanted put your credit in the document/spreadsheet

---

### Post by Elfy on 2011-06-22
moved to general help. Tutorials and tip sis not a place to ask for help.

There's more than one way to skin a cat - have a look on the openoffice help sites.

This was the first result from a google search for "open office help invoice numbering in writer"
[http://www.oooforum.org/forum/viewtopic.phtml?t=66639](http://www.oooforum.org/forum/viewtopic.phtml?t=66639)

---

### Post by amanchesterman on 2011-06-22
I don't use Libre Office, I use Open Office, but I believe they are very similar.

If I understand your post correctly, you want to put a sequential number on each invoice? i.e. the first invoice is (say) no. 0001, the second is 0002, and so on? Is that what you mean by a 'constant invoice number'?

If so, what you are trying to do is quite complex. In the link you quote, the author does it by inserting a number field in the document and then creating a macro that increases the number automatically. If you've never dealt with fields and macros, it would take you a long time to get this working reliably.

A much simpler option would be:
a) create a spreadsheet with a list of invoice numbers in a column - 0001, 0002, 0003 and so on
b) when your friend wants to create an invoice, he enters the details (name, address, amount etc.) in the columns beside the next unused invoice number
c) then he opens a blank invoice document that you have created, which has spaces for the invoice number, name, amount etc.
d) finally he copies-and-pastes the data from the spreadsheet into the invoice document and prints it.

That way he ends up with
i) invoices numbered in sequence and
ii) a record of all the invoices he has sent.

I know it's not as 'neat' as an automatically-generated number ... but what is wrong with doing things manually sometimes? 

John

---

### Post by maz32 on 2011-07-26
First off i would like to say im terribly sorry i have not responded as i only look in the tips and tutorials for a week and then gave up. Im also sorry for creating it in the wrong forum.

Few things

i tried that link forest and had troubles to get it to work. (as it was some time ago i will have to try it again to tell you what my problems were).

i was going to ask how to get open office back instead of Libra but i found a website and i have go back from work and its now late so i haven't tried it.

amanchesterman as this sound like a good idea i am trying to get it as simple as possible because the guy im doing it for is computer illiterate. so the less work he has to do the better. But thank you very much for the idea.

i have also seen that macros can be done in javascript and my uncle is a experienced programmer but i dont know how well he knows Linux. is it even possible to do what im after in a macro for OoO in javascript. 

i will have ago with some things i have found probably on the weekend and let you know how I go this time i will keep watching this thread now i know where it is.

Thanks to amanchesterman and forestpiskie and who ever else that has had a read of my problem and given me a hand its much appreciated

---

### Post by 2F4U on 2011-07-26
Would an accounting software with the capability to do invoicing too much for your neighbour? If not, you may wish to look at GnuCash:

[http://www.gnucash.org/](http://www.gnucash.org/)

---

### Post by mike555 on 2011-07-26
You might want to look at;     [http://bambooinvoice.org/](http://bambooinvoice.org/)

---

### Post by maz32 on 2011-07-27
using a program is also something i would like to explore but getting them to work on linux without risk data on the internet is a big issue and i haven't had much luck in the past. i was also going to put ubuntu 11.04 32 bit on fresh instead of 64 bit cause its no use. and i get a fresh start. 

i looked at gnu cash last night and failed to find somewhere to enter a stock list that's why i was doing it in a spread sheet using a v lookup.

bamboo invoices looks alright with our loading it up.

i am also going to try nevitium when i can get java to update (thats a different story though)  

thanks for your help guys

---

### Post by oldstumpy on 2011-10-07
Hello:Maz32 i was having the same problem couldn't
find a suitable software program for invoicing,until
i found this one it is not free,but only 29.99US i bought it and installed in ubuntu 11.04 it is very simple and works like a charm just thought this might help.Oldstumpy:p

---

