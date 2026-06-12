---
title: "Open/Libre Office and Microsoft Word: text spacing and display"
date: 2011-08-06
forum: General Help
---

### Post by amanchesterman on 2011-08-06
I have Ubuntu 10.10 and Open Office 3.2.1. I guess that this problem may affect Libre Office too, but I will be happy to be proved wrong about that. :)

I am editing a document that was originally produced in Microsoft Word (the standard .doc format). It is a form produced by a national organisation and it has to be sent back to them, and when submitted it has to be no longer than two A4 pages. It contains a series of headings and (expanding) text boxes for content.

In order to be sure about the length, I did most of the editing with Microsoft Word on my wife's laptop. On that machine, and on a PC that has a different version of Word, the document fits exactly within the two-page limit. But on my laptop, using Open Office, it appears considerably longer, taking up two-and-a-half pages.

Why is this, and can anything be done to correct it? Open Office appears to be using the same fonts as Microsoft Word - the font names are the same, anyway - and the font sizes are the same, yet the text appears to take up more of the page display.

Has anyone else encountered this problem, and has anyone found a solution? It is tiresome to have to go back to Microsoft Word when issues of spacing and layout are critical like this!

Thanks
John

---

### Post by TeoBigusGeekus on 2011-08-06
Check the boundaries of the page.
Also, go to Format>Page and check whether it is A4 or Letter size.

---

### Post by amanchesterman on 2011-08-08
Thanks for your response. It's not due to the page or paper size, nor to the font or font size, all of which are exactly the same in both Word and Open Office.

As far as I can see -- and I have now compared Word and Open Office side-by-side on two laptops -- the difference is in the way Open Office displays spaces between words. I have measured the letters with a ruler on both monitors and the actual words of the documents appear to take up the same width; but the spaces between words are wider in Open Office than in Word.

This isn't because the spacing characters are different: it's the same .doc file in both cases, and I have checked that the number of spaces between words (usually one space) is the same. It's because Open Office allocates more room to the spacing character than Word does.

Incidentally it appears to do this whatever font is used: the document has three different fonts in it, and the 'wide spacing' effect is noticeable in them all.

Does anyone know if it is possible to alter the width of the spacing character in Open Office, so that it displays text exactly like Word?

Thanks
John

---

### Post by notwhatmynameis on 2011-08-16
thanks for your research I am currently looking at the same issue. I will reply when I have any more info.

---

### Post by Zill on 2011-08-16
amanchesterman:  Ensure that the font(s) used support "[pair kerning]("http://wiki.services.openoffice.org/wiki/Documentation/FAQ/Writer/FormattingText/The_space_between_the_letters_in_a_word_seems_just_a_bit_too_wide._It_would_look_better_if_that_space_is_being_reduced._How_can_I_achieve_this%3F")" and that this is enabled.

This can be done either for selected text via Format > Character or for a style via Format > Styles and Formatting.

If this does not help then you may get better support directly from the [OOo forums]("http://user.services.openoffice.org/en/forum/").

---

