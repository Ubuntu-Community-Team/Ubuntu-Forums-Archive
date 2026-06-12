---
title: "identify unicode fonts"
date: 2012-03-24
forum: General Help
---

### Post by leonardjensan on 2012-03-24
Please excuse me if this is a basic query.

Is there a way for me to identity if a font I have installed supports Unicode? I need to identify my unicode (utf-8) fonts.
Warm Regards,

Leonard

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-24
What exactly do you mean by "font supporting Unicode"?

---

### Post by leonardjensan on 2012-03-24
maybe I have worded myself wrong. I need to know if a font is a Unicode font. Any utility that will help me do that.

I wonder why some fonts show the alphabet when double-clicked while others show squares.

Warm Regards,

Leonard

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-24
If a font doesn't contain a certain set of characters (i.e. if it shows boxes instead of letters), it does not mean that that font is not a Unicode font. Unicode standard has over 110.000 characters, and a vast majority of Unicode fonts do not cover the entire range of Unicode spec. Most Unicode fonts cover only a few hundred characters. In other words, it doesn't mean that, if a font doesn't contain a certain set of characters, it doesn't "support" Unicode, and vice versa, if a font "supports" Unicode, it doesn't mean that it will contain every single character from Unicode spec.

It would help if you mention which specific Unicode range is of interest to you (Latin, Cyrillic, Greek, Hebrew, Arabic, some other?), which fonts create problems to you (show boxes instead of letters), and in which programmes does that occur.

In general, Character Map (comes pre-installed in Ubuntu) can help you determine which characters do or do not exist in a certain font. Also, there are many Font managers to download and install (try searching the Software Centre), and most of them can help you do the same.

---

### Post by leonardjensan on 2012-03-24
Thank you. While that explains a lot, it also throws up a lot of questions. If I am asking too many questions and intruding on your time, please point me to a source of information.

I am using Calibre to convert a PDF document into epub. The PDF document reads fine but the resultant epub does not (it reads gibberish). I thought maybe changing the font to a "unicode font" will help me but that did not happen. What are my options? Which font do I use?

Another question. Suppose I am typing Tamil and I want to change the font. When I do so, the Latin equivalent appears although I know for sure that the fonts has a character map for Tamil. Is there a way to force a font to use a particular character set?

Thank you very much!!!

= Leonard

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-24
Don't worry, you're not asking too much. I will try to help you as much as I can.

Unfortunately, I haven't used Calibre, so I don't know what the problem might be. However, the source of the problem might be within the PDF. It often happens that non-unicode fonts are used to create PDFs, which later makes it impossible to convert such PDF document to another format (doc, epub, html) or even copy the text from it. Also, I don't know  which Unicode fonts contain Tamil range. It is possible that some of the [Microsoft Web Core fonts]("http://en.wikipedia.org/wiki/Core_fonts_for_the_Web") support it. Also, check if Ubuntu font contains Tamil range.

What you can do is, if you're the creator of PDF, try with a different font, for which you are certain contains Tamil range. If that doesn't help, then the same problem might exist in the font used within the target epub document, so try also changing the target document's font to the one you are sure contains Tamil range.

---

### Post by leonardjensan on 2012-03-24
Also, why do some fonts show the text when double-clicked in Font Manager while others show blank squares?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-24
> **leonardjensan said:**
> Also, why do some fonts show the text when double-clicked in Font Manager while others show blank squares?

It means that those fonts which show squares instead of letters do not contain the character range used to type the given text.

---

### Post by leonardjensan on 2012-03-24
Thank you very much indeed. This helps a lot!

Okay...so I go back to the doc that I used for the PDF and try to replace it with a font that I know has a Tamil Character Map. But instead of replacing with the Tamil Character Map, it uses the Latin Character Map and I am left with a whole bunch of gibberish. How do I force the font to replace in Tamil and not Latin.

Thank you for your time.

= Leonard

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-24
I'm not sure I got that right. If I may rephrase: you have a text written in Tamil in a doc file. When you select the entire text and change the font, all the letters turn from Tamil into Latin. Is that correct?

---

### Post by leonardjensan on 2012-03-26
Yes, that's exactly the problem.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-02
Sorry bro, didn't see you replied.

Unfortunately, this looks to me as the least good case. That means that a non-unicode encoding was used to create the original doc file. For me to help you any further, it would help very much if you could attach the document in question. If that is not possible, a sample or a similar document would do (one which uses the same encoding).

---

### Post by leonardjensan on 2012-04-13
Now it's my turn to apologize. I was on the road and had little access to the Internet.

I have attached a Tamil file. Any help is appreciated.

Warm Regards,

Leonard

---

### Post by Vaphell on 2012-04-13
i read a bit and tamil sounds like a disaster when it comes to encodings and char tables - there are quite a few.
You need to find out which encoding was used in original document. How was the source created?
Can you test what happens with plain text file created in original environment when opened in linux? Plain text is much better to track encoding issues, as the data is not obfuscated like in the case of document formats and you can try opening it with any encoding possible with no problem.

---

### Post by leonardjensan on 2012-04-18
I was wondering about that too. Do you think it is always a better idea to have the text typed out as a plain text file rather than a doc file?

Thank you for your help.

---

### Post by Vaphell on 2012-04-18
if you need formatting and have to show it to someone else, obviously not.
But if you are just typing things down, sure. Using plain text you have much smaller files and it's much easier to convert between encodings and what not when you compare it to more advanced programs that bury that info deep and lose it during transitions and conversions.

Could you attach some small sample plain text file from the same source (windows machine i assume)? that would help to investigate what needs to be done to transcode the text properly.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-18
If I may add to that, it is always a better idea to have a text typed as plain, and it is also important to use UTF-8 encoding when saving any document, in case the document is intended to be communicated later on (transferred from the originating machine to another medium). Rich text formatting is useful for documents that are intended to be printed right away or converted to .pdf, but as we're seeing in this example, even in the latter case problems can occur.

---

### Post by leonardjensan on 2012-04-24
I appreciate your suggestions. Would it be accurate to say that text should preferably typed in a text file with UTF-8 encoding and then "decorated" according to the purpose it will serve? That the "base" should be typed into a text file?

Thank you for your help,

Leonard

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-24
Yes, you could say that. It is one safe way to do it.

---

### Post by leonardjensan on 2012-04-24
Thank you. If you have other ideas, let me know.

Regards,

Leonard

---

