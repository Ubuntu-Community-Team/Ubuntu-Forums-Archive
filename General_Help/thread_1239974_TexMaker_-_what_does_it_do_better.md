---
title: "TexMaker - what does it do better?"
date: 2009-08-14
forum: General Help
---

### Post by longtom on 2009-08-14
Hi,

in some thread around here people were discussing office suits and word processors in particular.
Those, who seem to be or wanted to be identified as professionals or doing work like professionals, were repeatedly referring to Laytex.  

So, always in line to make up a document like most of us, I got onto the website, downloaded Texmaker and started reading the documentation.

Somehow I don't get it (common occurrence).  What does it do better than OO Word Processor?  Why would this:

[img]http://ubuntuforums.org/attachment.php?attachmentid=124812&stc=1&d=1250241709[/img]

be more complicated than this:

[img]http://ubuntuforums.org/attachment.php?attachmentid=124813&stc=1&d=1250241709[/img]

I found quite some documentation how to do Laytex - I haven't found too much explaining to the layman (or anybody) why one would use it.

Will I benefit from it writing up memos and other work related documentation?  
Will it make my letter to granny look better? (or even write it by itself?)
Is it only useful for BIG documents?
How can it make you CV look better (as some have claimed)?

I know - you are probably rolling your eyes backwards - but I am at a loss - somewhat.

Please try to explain to the uninitiated....

---

### Post by Irihapeti on 2009-08-14
Here is my opinion, and I'm sure there will be many who disagree with me.

The point about LaTeX is that it gives typeset-quality output. It uses typesetting algorithms to render the document to PDF. If you create a document in LaTeX and the same thing in OpenOffice and compare the printouts, you'll see a difference.

If you were publishing an article in a scientific journal, you would get hold of a style sheet for the publication and all your margins, headings and so on would be the right size and style. You would just have to a paragraph as a heading or a subheading or whatever, and the details would be sorted out for you.

You can actually use LaTeX for documents of any length, and some people do. It is great for long documents with headings, subheadings, footnotes, mathematical formulae, bibliographies and so on. If I were writing a book or a dissertation, I'd use it. I have even read stories about people being able to print off their thesis which they had originally done in LaTeX 20 years ago. I think that might be hard to print off a 20 year-old word processing file.

For a brief memo, a letter to my son, a meeting agenda, or a notice to put up on the community notice board, I'd probably use OpenOffice writer. I can just open a blank document and start typing.

For something like a brochure or a fancy leaflet with graphics in it, I'd use a layout program such as Scribus or OpenOffice draw so that I can get all the bits and pieces in the right places.

There is also a program called LyX (in the repositories) which is a sort of front end to LaTeX. I dare say that 'real men' will scoff at it, but it can be a good way to get started. It's kind of half way between a word processor and LaTeX. If you get really keen, you can always switch to using LaTeX on its own with vi, emacs, nano etc :):)

---

### Post by longtom on 2009-08-14
> **Irihapeti said:**
> 
For a brief memo, a letter to my son, a meeting agenda, or a notice to put up on the community notice board, I'd probably use OpenOffice writer. I can just open a blank document and start typing.

For something like a brochure or a fancy leaflet with graphics in it, I'd use a layout program such as Scribus or OpenOffice draw so that I can get all the bits and pieces in the right places.


Thanks for your input.  Above is what I thought.  So if I am not writing a thesis or a book or publish in a scientific journal, it wouldn't make sense to use it?

---

### Post by bchurchill on 2009-08-14
In addition, the real power of LaTeX is in scientific documents where you have complicated symbols and tables.  As a student studying mathematics, I've used LaTeX to do my homework for the last four years, and I guarantee you it is the fastest way to typeset anything complicated, even if it's not intuitive.  As you learn the language of LaTeX you get much faster after you surpass the steep learning curve.  After practice, one can type complicated LaTeX code about as quickly as normal text.  Right now, it takes me about 10 seconds to type:

```

$\lim_{x \rightarrow \infty}\int_0^x{\frac{dx}{3x^2 + 4 -\sin(x)}}$

```which produces...

[IMG]http://www.berkeleychurchill.com/misc/eg.gif[/IMG]

(I created this image using [http://www.artofproblemsolving.com/LaTeX/AoPS_L_TeXer.php](http://www.artofproblemsolving.com/LaTeX/AoPS_L_TeXer.php)... a very convenient bookmark to have)

but I bet it would take a long time to make an image of nearly that quality in any WYSIWYG editor.  If you have even more complicated things, like commutative diagrams that include lots of symbols then LaTeX is the only reasonable way to make them.  The person who made the is quite skilled, but it's an excellent demonstration of LaTeX.  It probably didn't take him/her to make it either:

[IMG]http://www.typophile.com/files/three-cat_5079.gif[/IMG]

(I didn't create this... came from google search)

Of course, this isn't just useful for mathematicians.  Chemists, linguists, computer scientists, physicists and others all use it for technical documents.


Moreover, LaTeX has performance benefits: you don't have to render anything so it's possible to generate very long, complex documents on systems with restrained resources.  Even on modern systems long complex documents can be difficult to manipulate and maintain a 200-page manuscript filled with equations.

Also LaTeX has every symbol you can imagine built in or available as an extension (usually built-in).  Yes, even more than Open Office or Microsoft Word.

Once you've done a few documents in LaTeX you'll have templates for your other ones so you won't have to write all that \documentclass.........  stuff every time, and you can get to the meat of \begin[document]...\end[document]

LaTeX also takes care of all the whitespace for you.  I rarely need to manage whitespace manually because the LaTeX interpreter makes it look good.

Extensions to LaTeX include BibTeX (sp?) which allows one to add biblographic citations seamlessly to your work without making it cluttered.  Other perks include automatically-generated tables of contents for books and the like.

The list goes on.... :)  I love LaTeX.

---

### Post by bchurchill on 2009-08-14
> **longtom said:**
> So if I am not writing a thesis or a book or publish in a scientific journal, it wouldn't make sense to use it?

Unfortunately I didn't see this before my last post.

I'd say no.  There are many times that you want to use LaTeX.  In general I use it whenever I'm making a document that doesn't need eye-catching glitter, but most people probably would use it when it's faster than your typical office software (e.g. when you have complex stuff to typeset).  I use it all the time for documenting software, doing homework or answering math questions via email.

Then again, you probably don't want to use LaTeX if you're just writing a quick note to somebody.

---

### Post by longtom on 2009-08-14
> **Irihapeti said:**
> 
There is also a program called LyX (in the repositories) which is a sort of front end to LaTeX. I dare say that 'real men' will scoff at it, but it can be a good way to get started. It's kind of half way between a word processor and LaTeX. If you get really keen, you can always switch to using LaTeX on its own with vi, emacs, nano etc :):)

Let the real men battle it out by themselves.  I checked out LyX and am pleased, that it does come with a big bundle of documentation.  

So I'll work my way through that and hopefully will understand a bit more what the fuss is about.

Thank you for mentioning LyX.

---

### Post by XCan on 2009-08-14
Obvious: Simply put Latex by default produces text that are both very readable and beautiful. Word and its equivalents do neither. Their default template seriously break the typographical rules and produce text that are much less readable due to retarded font selections, line widths and line spacings.

When it comes to mathematical formulation, latex is superior. It will produce beatiful expressions, and you don't even need to click in one million boxes to do it, it's simply faster.

Another huge advantage with latex is that you can easily insert and resize-online vectorized graphics, no more pixelation due to enlargement, and no need to save images in some ultra-high resolution. When we're talking about figures, which are floats, let's not forget the tables produced by latex. You just have no chance to produce production-like tables using Word with so little effort.

What's more, labling, citing, bibtex, the list goes on. Once you learn it, you wonder how people can keep using with Word when they are writing up something serious. 

The most important with latex is that the author can focus on the text and its contents, instead of stupid layout annoyances which we all know from Word. Granted, as mentioned above, if you're just writing up a note, latex may be overkill. But if it's supposed to be read by many people, just forget Word.

---

