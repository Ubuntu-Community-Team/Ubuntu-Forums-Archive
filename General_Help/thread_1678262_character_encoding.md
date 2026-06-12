---
title: "character encoding"
date: 2011-01-30
forum: General Help
---

### Post by light-vessel on 2011-01-30
I have file names that include Czech and Polish characters and I also browse websites that use various characters not used in English. Ubuntu doesn't recognise these and neither does Firefox. All I want to do is find and install something that allows these file names and shows these characters. I don't even know where these settings are in Ubuntu. Any help would be appreciated. If it could be made simple, help would be greatly appreciated.

I use Ubuntu Lucid.

---

### Post by tredegar on 2011-01-30
I am running 10.04 and all character sets seem to be recognised and displayed correctly: Chinese, Russian, Greek, Thai, Czech, Portugese, French ....

I did not have to do anything special for this to happen.

My LANG settings are set to use utf8 encoding:
```
echo $LANG
LANG=en_GB.utf8
echo $GDM_LANG
GDM_LANG=en_GB.utf8
```

---

### Post by light-vessel on 2011-01-30
Thanks. I think I must have saved the files on a system with different encoding and some websites or posters on websites also use other encoding systems that aren't compatible.

But how would I change from utf8 if I wanted to?

---

### Post by tredegar on 2011-01-30
If you want text from different languages to render properly, I think you *need* utf-8

What happens when you type this in a terminal?
```
echo $LANG
echo $GDM_LANG
```
Can you post a link to a site that doesn't display properly for you?

Filenames can be converted to utf-8 with the **convmv** utility.

A lot of people seem to have trouble with the names of music files being copied from windows systems, is this your problem?

---

### Post by light-vessel on 2011-02-19
I don't have any examples I can show. One problem is with passwords for rar files. When certain characters are used, Ubuntu doesn't recognise them so I have to take them to another computer. I know I'm not the only person with this problem - someone I have shared audio files with has exactly the same problem when using Ubuntu.

---

