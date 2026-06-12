---
title: "[localization] CJK collation in unicode order possible?"
date: 2011-06-08
forum: General Help
---

### Post by Raito on 2011-06-08
Alright, so I have files in my computer with filenames in Chinese (traditional and simplified), Japanese, Korean, and more, sometimes even in the same folder. (My music folder for example)

The only problem is, I can't seem to find a usable CJK collation that works with all 3 languages. I want all CJK to be behind ascii, Japanese kana and hangul to be sorted by the standard phonetic way, and Chinese characters to be sorted in /some/ way, though I seriously don't care what. (I'd prefer pinyin or unicode-style kangxi)

In Archlinux, my old distro this was easily achievable by simply having an en_XX locale, and everything would be sorted in the order that they are in unicode. However, in ubuntu:

en_XX locale gives Japanese and Korean in a very strange order and places it before ascii. 
zh_XX gives Chinese in pinyin and Japanese and Korean in a very strange order and places it before ascii.
jp_XX gives kana in an good order, Chinese in a poorly implemented Japanese style order, and Korean before ascii
ko_XX seems to be almost the most usable, where everything is perfect except simplified Chinese being placed before ascii

So none of these options work for me.

Is there any way to have things in a simple unicode order? Thanks.

EDIT: LC_COLLATE=C gives me the perfect order. I guess I'll put this in my .xinitrc once I figure out how to make one.

---

