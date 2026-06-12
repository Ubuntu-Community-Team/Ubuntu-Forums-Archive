---
title: "spell check for firefox and thunderbird &amp; others."
date: 2012-01-23
forum: General Help
---

### Post by yoramdavid on 2012-01-23
Hi all,

I use several spell checkers (for different) languages and programs. From time to time I add a word to a dictionary. I would like to save these files for future use in new installation of Ubuntu.
The spell checkers I need are from Firefox, Thunderbird, Pidgin and LibreOffice.

Where do I find them?

Thank you

---

### Post by dcstar on 2012-01-24
> **yoramdavid said:**
> Hi all,

I use several spell checkers (for different) languages and programs. From time to time I add a word to a dictionary. **I would like to save these files for future use in new installation of Ubuntu.**


Then use a separate /home partition.

---

### Post by decrepit on 2012-01-24
Until you're next installation, (when you create a separate home partition).

Firefox and thunderbird stuff is in your home folder, under .mozilla and .mozilla-thunderbird. To see in nautilus, click view/show hidden files

Don't know about the others, but I bet they're in a similar place.

If you save these folders, then copy them into your new home folder, all your inboxes, address books, and bookmarks, will be there as well.

---

### Post by yoramdavid on 2012-01-24
Separate home folder, is it?
Or save its contents and replace what I want.

Thanks. Do you know exactly which file saves this spell-check entries for firefox and thunderbird?

---

### Post by Krytarik on 2012-01-24
Coincidentally, as I've just started to use spell checking myself, I was asking me the same just earlier today; here you go :D :

[LIST]
[*]**Firefox / Thunderbird**: the file "persdict.dat" in the top-level of your profile directory.
[/LIST]

[LIST]
[*]**LibreOffice**: I only have OpenOffice.org installed, but, with adaption of the name of its top-level directory, it should be located similar to "~/.openoffice.org/3/user/wordbook/standard.dic" ("standard.dic" is the default dictionary to save custom additions in OpenOffice.org).
[/LIST]

[LIST]
[*]**Pidgin**: depending on the languages you use for spell checking, files like "~/.config/enchant/en_US.dic".
[/LIST]
Those files of Firefox, Thunderbird and Pidgin are all plain text files, and can be edited to add or remove words.

Regards.

---

### Post by yoramdavid on 2012-01-25
> **Krytarik said:**
> Coincidentally, as I've just started to use spell checking myself, I was asking me the same just earlier today; here you go :D :

[LIST]
[*]**Firefox / Thunderbird**: the file "persdict.dat" in the top-level of your profile directory.
[/LIST]

[LIST]
[*]**LibreOffice**: I only have OpenOffice.org installed, but, with adaption of the name of its top-level directory, it should be located similar to "~/.openoffice.org/3/user/wordbook/standard.dic" ("standard.dic" is the default dictionary to save custom additions in OpenOffice.org).
[/LIST]

[LIST]
[*]**Pidgin**: depending on the languages you use for spell checking, files like "~/.config/enchant/en_US.dic".
[/LIST]
Those files of Firefox, Thunderbird and Pidgin are all plain text files, and can be edited to add or remove words.

Regards.

Thank you Krytarik,

Firefox and Thunderbird:
I found those for Firefox and Thunderbird where you said there were.
I switched to English spell-checking to write this text and added "Thunerbird" to the list and I went to check into the "persdict.dat" and it was added indeed.
I then switched to Portuguese check-spell and added a word but it did not appeared there, **I wonder where it stores the words for other languages.** I am now doing a search for the word to see if I can find the file.

LibreOffice is inside: ".libreoffice/3/user/wordbook/" witht the same name you mentioned. I have to find out where it stores other languages words too. I saw that there is a line about "lang: <none>". I wonder if it will store the other languages in the same file under a different heading.

Pidgin: could not find it. There is no .pidgin folder, pidgin stores its files under .purple, right? But there is nothing there either. I did a search in there for the words "enchant" and "en_US.dic" but found nothing.
Where exactly is it?

Thanks

---

### Post by Krytarik on 2012-01-25
Ok, I've just checked how the various apps are handling custom additions when using multiple languages; here you go again :D :

[LIST]
[*]**Firefox / Thunderbird**: Unfortunately, they aren't properly supporting custom additions for multiple languages, they are throwing all additions in the same file. And they are saving the additions only to that file upon closing, that's why you haven't found your addition earlier, I presume.
[/LIST]

[LIST]
[*]**LibreOffice**: Supports saving the custom additions in different dictionaries, for which you can set the respective languages (the default is "All"). You can add dictionaries or change their language via "Tools -> Options -> Language Settings -> Writing Aids" or via the "Options" in the "Tools -> Spelling and Grammar" dialog (based on my OpenOffice.org install). They all end up in the same directory stated before.
[/LIST]

[LIST]
[*]**Pidgin**: First, the dictionaries aren't saved under the Pidgin profile directory (yeah, would be "~/.purple"), but exactly in the directory I've stated before, "~/.config/enchant". And as the language-dependent file names I've mentioned before already indicate, Pidgin supports multiple dictionaries, they obviously end up in the same directory, too.
[/LIST]

---

### Post by yoramdavid on 2012-01-25
> **Krytarik said:**
> Ok, I've just checked how the various apps are handling custom additions when using multiple languages; here you go again :D :

[LIST]
[*]**Firefox / Thunderbird**: Unfortunately, they aren't properly supporting custom additions for multiple languages, they are throwing all additions in the same file. And they are saving the additions only to that file upon closing, that's why you haven't found your addition earlier, I presume.
[/LIST]

[LIST]
[*]**LibreOffice**: Supports saving the custom additions in different dictionaries, for which you can set the respective languages (the default is "All"). You can add dictionaries or change their language via "Tools -> Options -> Language Settings -> Writing Aids" or via the "Options" in the "Tools -> Spelling and Grammar" dialog (based on my OpenOffice.org install). They all end up in the same directory stated before.
[/LIST]

[LIST]
[*]**Pidgin**: First, the dictionaries aren't saved under the Pidgin profile directory (yeah, would be "~/.purple"), but exactly in the directory I've stated before, "~/.config/enchant". And as the language-dependent file names I've mentioned before already indicate, Pidgin supports multiple dictionaries, they obviously end up in the same directory, too.
[/LIST]

Wonder why  my earlier search for "enchant" did not return any results then. I got confused by the "~/", ok it stands for the home folder, I should have know that.

OK, found them all now. Thanks a lot.

---

