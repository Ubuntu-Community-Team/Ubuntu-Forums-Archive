---
title: "HowTo: Quick translation help"
date: 2009-07-17
forum: General Help
---

### Post by elektronaut on 2009-07-17
Hi,

I finally got back to solve my translation problem described [**in this archived thread**](http://ubuntuforums.org/showthread.php?t=737560). Back then I didn't understand [**pointone**](http://ubuntuforums.org/member.php?u=244028)'s post, partly because I didn't find the 'translator' tool and assumed that it was just meant as a placeholder. Anyway, here's the [COLOR="Red"]**one-keystroke solution**[/COLOR] for translations from every application which is based on his suggestions:

1. You need libtranslate-bin, a cool command line translation program.
```
sudo apt-get install libtranslate-bin xsel
```

2. Then you need a script which reads the clicked word(s), calls libtranslate-bin, and displays a pop-up with the translation. Copy the following script to your hard disk (I recommend to keep all scripts in a folder in your home directory so you don't lose them when you migrate - I put them all in ~/bin/):
```
#!/bin/sh
# quick-translate.sh
# translates words quickly
# see http://ubuntuforums.org/showthread.php?t=1215650

TRANSLATION=$(xsel | translate-bin)
zenity --info --text "$TRANSLATION"

# only needed if you want to store the translated word(s) in the clipboard
echo "$TRANSLATION" | xsel --clipboard -i

exit 0
```

Don't forget to make it executable:
```
chmod +x bin/quick-translate.sh
```

3. The final step is to add the shortcut as described [**in this blog post**](http://justanothertechblog.blogspot.com/2006/12/defining-keyboard-shortcuts-in-gnome.html) (Thanks again, pointone!).

So now all you have to do is double click a word, press the assigned key shortcut, and voilà, the translation pops up and is also in the clipboard! For customization, e.g. changing the "from" and "to" languages, you might want to look at the 'man page' for translate-bin. For example, you can set the environment variables "TRANSLATE_DEFAULT_TO" and "TRANSLATE_DEFAULT_FROM".

---

### Post by elektronaut on 2009-07-17
If somebody has some information about a good way to get the translations into a vocabulary list or even a program for vocabulary learning, I would be pleased to hear about it!

---

### Post by elektronaut on 2009-07-17
So far, I've come up with a new script for translations from english and french (I set the default 'to-language' to german):
```
#!/bin/sh
# quick-translate.sh
# translates words quickly
# see http://ubuntuforums.org/showthread.php?t=1215650

ORIGINAL=`xsel`
TRANSLATION_EN=$(xsel | translate-bin -f en)
TRANSLATION_FR=$(xsel | translate-bin -f fr)
TRANSLATION=$(zenity --title "Choose the correct one" --list --radiolist --column "Choose" --column "Translation" --column "Language" TRUE $TRANSLATION_EN English FALSE $TRANSLATION_FR French)

# only needed if you want to store the translated word(s) in the clipboard
echo "$ORIGINAL;$TRANSLATION" | xsel --clipboard -i

exit 0
```
Now you have to choose the correct translation, according to the original language. The language pair in the clipboard can be added to [**Parley**](http://edu.kde.org/parley/), which is apparently a very good vocabulary trainer. Would be cool though to automate this. At the moment you still have to go to the Parley window and then paste the language pair.

---

