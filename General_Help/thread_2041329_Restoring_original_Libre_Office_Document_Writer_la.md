---
title: "Restoring original Libre Office Document Writer layout"
date: 2012-08-12
forum: General Help
---

### Post by tnob on 2012-08-12
[FONT="Arial"][/FONT]

Greetings all.

This is about a minor, but highly annoying problem concerning text processing, affecting months of previous work.

With my usual platform (Ubuntu Dream Studio 12:04) temporarily out of order, I had to resort to Windows XP's Rich Text Format to continue work on a manuscript currently underway. Once access to Libre Office Writer was back, however, I discovered - much to my dismay - that the layout had changed completely. Most notably, sentences are now ending in the wrong place: 'have', for instance, becomes 'hav e'.

Apart from copying the whole lot by hand over all over again, I don't know what else to do to restore the document to its original (i.e. justified) state. Any suggestions?

Thanks very much!

tnob

---

### Post by cottfcfan on 2012-08-12
If this is what you mean.
To set Libreoffice back to default, and delete any changes you have made you need to delete the /Home/.config/libreoffice folder.

---

### Post by Jay MC on 2012-08-12
I think he's talking about the formatting of an individual document, rather than his settings for the app itself.

OP - having slight problem understanding what the problem is.  The "have" - "hav e" thing sounds like extra spaces are being inserted to words, but you also talk about the justification of text.  Is the problem that the lines are ending in the wrong places, sometimes mid-word?

Example, like this blo
ck of text that I've d
one here?

Or is it something else and I've misunderstood?

Generally how is your document formatted?  If it needs correcting in a predictable way, then someone may be able to help you fix it using Find & Replace (for instance, using regular expressions, I could quite easily fix the example I gave above).  Could you provide a few sample paras?

---

### Post by tnob on 2012-08-16
[I]Quote: Is the problem that the lines are ending in the wrong places, sometimes mid-word?

Example, like this blo
ck of text that I've d
one here?[/I]

Yes, Jay MC, that is exactly what the problem is.

Because Ubuntu was temporarily out of order, I had to continue on Windows XP (in Rich Text Format). But on returning to Ubuntu the document was complety messed up in the way you illustrated.

Any idea of how to fix this?

Thanks very much!

tnob

---

### Post by Jay MC on 2012-08-19
Okay - I've had a play with the find-and-replace on LibreOffice, and it seems a bit dicky to me, but let's try a couple of things.

Say your text looks like this, with each para separated by a blank line, but random line breaks within each para:
[I]
Example, like this blo
ck of text that I've d
one here?

How do I fix this blo
ck of text?  The ans
wer is to use regex.[/I]

Do find and replace.  Show more options, and tick "regular expressions" (aka regex).

Now replace $ (which means the end of a paragraph) with nothing.  When I do that, I get this:

[I]Example, like this block of text that I've done here?
How do I fix this block of text?  The answer is to use regex.[/I]

Which isn't quite what I expected, but never mind.  I can now use paragraph settings to either indent each paragraph or put spaces between them, or whatever.

Like, I say, the regex seems a bit dicky to me, and I'm not entirely sure why that works as well as it does (where there are two carriage returns on the trot, it seems to only replace one of them...  which is fortuitous, but I'm not sure why it's doing it - unless it's reading my mind!).  And of course, if you don't have white space between your paras, you may find that you lose genuine line breaks along with the unwanted ones.  Either way, give that a go and see if you have any problems.

You can read about the special characters and formula that you can use in regex [here]("http://help.libreoffice.org/Common/List_of_Regular_Expressions").

Genuine sample paras would be helpful (if privacy is an issue, perhaps you could replace half the words with nonsense ones?).

---

