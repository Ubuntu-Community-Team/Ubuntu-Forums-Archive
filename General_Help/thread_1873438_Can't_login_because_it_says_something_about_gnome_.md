---
title: "Can't login because it says something about gnome not being configured"
date: 2011-11-01
forum: General Help
---

### Post by RabbitWho on 2011-11-01
Gnome is configured, I know this because when I tried 20 times it let me in once. 
I also figure gnome can't be the problem because it **won't let me into Xterm** or Lubuntu either (Same partition). 

I thought it might be because there was no space on the drive, so when I finally got in that one time I tried to delete some files, it said they didn't delete, I clicked delete and nothing visible happened.

I went into windows, I got EXT2 volume Manager and it said I had 7GB of free space, as if i had deleted those files. mounted the linux partition, looked at the files, tried to delete a movie, it told me I couldn't delete it because I didn't have write permission and then when I looked again I had 13GB of free space. 

I'm using Lucid Lynx 32bit. 

Is this all just a free space problem that will go away if I can delete the files properly from a live disk?

---

### Post by Gatemaze on 2011-11-01
Are you referring to your home directory? Wild guess your userid is different from the one that the directory belongs to? A simple ls -l will show you the id the dir belongs to. Either change your id using usermod or the ownership of the dir.

---

### Post by RabbitWho on 2011-11-01
>  			 		   		 		 		Are you  referring to your home directory? Wild guess your userid is different  from the one that the directory belongs to? A simple ls -l will show you  the id the dir belongs to. Either change your id using usermod or the  ownership of the dir.


You will notice, as it was in bold, that I couldn't get into the terminal. So where was I supposed to type that? 

Anyway it seems like it was a space issue, as i got in with parted magic and deleted 7GB worth of stuff and now it works.. but the funny thing is I should only have 7GB more space but I have 23GB more space, so I'm going to check for blocks or hard drive damage, that's all I can think of. 

Things are working now. 
[LEFT][COLOR=#FFFFFF][FONT=Trebuchet MS]exactly
[/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[LEFT]Detect language » English[/LEFT]


[/COLOR][/CENTER]
[LEFT][COLOR=#FFFFFF][FONT=Trebuchet MS][/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[LEFT]Detect language » English[/LEFT]


[/COLOR][/CENTER]

---

### Post by RabbitWho on 2011-11-01
Things are working so so well that I felt like listing out some languages *facepalm* 
[LEFT][COLOR=#FFFFFF][FONT=Trebuchet MS][/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[LEFT]Detect language » English[/LEFT]


[/COLOR][/CENTER]

---

### Post by Gatemaze on 2011-11-01
> **RabbitWho said:**
> You will notice, as it was in bold, that I couldn't get into the terminal. So where was I supposed to type that? 

1. If you could go to a terminal from ctrl+alt+f1
2. Boot from a live cd and troubleshoot linux issues with linux instead of using your windows partition.

---

