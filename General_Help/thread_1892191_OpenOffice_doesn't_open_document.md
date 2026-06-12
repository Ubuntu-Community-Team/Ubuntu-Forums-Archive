---
title: "OpenOffice doesn't open document"
date: 2011-12-07
forum: General Help
---

### Post by sonialiggi on 2011-12-07
Hello,

I'm working on Ubuntu 10.04.3 LTS, OpenOffice.org Word Processor Version: 1:3.2.0-7ubuntu4.2 

I'm having troubles opening my thesis, a .doc document created with OpenOffice, I hope you can help me!

yesterday, as usual, I saved the document in .doc format (97/2000/XP), but apparently something went wrong during the saving process since today I'm unable to open it, and moreover its dimension is too big (4.2 MB, too much for 20 pages).

If I try to open it from command line it said:

I18N: Operating system doesn't support locale "en_US"

So I tried several solutions I found on the internet:

a)
$cd /usr/share/locale
$ln -s en_US.ISO8859-15  en_US

but nothing changed

b)
i opened the file /var/lib/locales/supported.d/en and added the line "en_US UTF-8", then run:
dpkg-reconfigure locales

Now it doesn't generate the error anymore, but it doesn't open the file either!

Do you have any suggestion?

---

### Post by click4851 on 2011-12-07
just to determine whether its a problem with the file, or open office, have you been able to open your thesis with another document viewer? Also have you tried to open another known good doc file with open office?

---

### Post by sonialiggi on 2011-12-07
Yes, I've tried to open it with Microsoft office and it opens the "File conversion" window, asking to specify "the encoding that makes your document readable". I've tried all the encodings, without any success.
And yes, it opens without any problems other files, that's why I think the problem happened during the saving process.

---

### Post by kamaji792 on 2011-12-07
[edit] Completely got the wrong end of the stick - deleted original[/edit]

You can open an OpenOffice document in some file compression systems.  That may give you something to play with.

Atb k

---

### Post by sonialiggi on 2011-12-08
Hi kamaji792, I'm not sure I understood...what do you mean with open the document in a file compression system?
Thanks

---

### Post by click4851 on 2011-12-08
I'm trying to stay positive here....I would try to open the file in a program called Abiword which you can get from the Synaptic. Also how is your access to MSwindows machine? You could try to use Wordpad or Notepad to open the file, you would lose formatting but possibly recover most or all of text.

---

### Post by sonialiggi on 2011-12-08
Thanks click for your suggestions, but also abiword doesn't recognise the format :(

---

### Post by kamaji792 on 2011-12-08
Bah!  I was not having a good night last night.

You did say it was a .doc file.  which is not stored in a zip archive (.odt ones are).

In days past I used to use OpenOffice to clean corrupted Word documents, which they did reasonably successfully.  I see you have already tried opening it in MS Word.

I can't think of any other tricks apart from open the file in a plain text editor and extracting the text (I'd use vim but I guess any odd text editor should do the job).

Sorry I am not really being helpful

atb k

---

### Post by sonialiggi on 2011-12-09
Thanks everybody for your help, but there's nothing to do...apparently it's because of a bug in openoffice [http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=17677](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=17677)

---

### Post by Hagar Delest on 2011-12-16
Please remember also that the .doc import/export filters have been reverse engineered, hence some flaws. For such an important document like your thesis, you should have used the native ODF and exported when needed in .doc. The .doc format is proprietary and poorly documented. This is the vendor lock-in policy used by MS to keep their market shares.

If you need to work in .doc, then stick to MS Office, there is no other choice. OOo is not a free replacement of MS Office.

Note that the bug you've linked is more related to corner case involving especially power failure during save operation.

---

