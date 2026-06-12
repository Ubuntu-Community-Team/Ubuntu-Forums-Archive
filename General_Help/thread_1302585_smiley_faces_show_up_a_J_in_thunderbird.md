---
title: "smiley faces show up a J in thunderbird"
date: 2009-10-27
forum: General Help
---

### Post by shadowfoxx on 2009-10-27
Hello all,

I have limited experience with Ubuntu and Thunderbird. Ever since I have had it installed thunderbird displays smileys in emails I get as "J". I am not sure why but if anybody knows how to fix this please let me know. I have searched the interwebz and search function on this site but could not find anything... I know it's a stupid thing to worry about but it's kind of driving me crazy now.

---

### Post by Giblet5 on 2009-10-27
Thunderbird doesn't dress text smileys with a graphic icon like some IM clients do.

Thunderbird = serious
IM client = play

Sometimes, a J is just a J, even when it's preceded with hair and eyeballs as in *8J, and an email client is not the place to (mis)interpret what others write.

That said, you can easily write your own plugin to reinterpret text smileys and replace the text with animated icons.

---

### Post by QLee on 2009-10-27
[QUOTE=Giblet5]Thunderbird doesn't dress text smileys with a graphic icon like some IM clients do.[/QUOTE]

Isn't there a preference that can be set for "Display emoticons as graphics"?

[QUOTE=Giblet5]Sometimes, a J is just a J, even when it's preceded with hair and eyeballs as in *8J, and an email client is not the place to (mis)interpret what others write.[/QUOTE]

And sometimes a J is because the mail was sent in a font that is not available to the system that received it. For example, Capitol J (unicode 004A) in the wingdings font (a font usually standard on Windows systems) is a normal smiley face. Perhaps that's what your correspondent was meaning to send shadowfoxx.

---

### Post by shadowfoxx on 2009-10-27
thanks for your input QLee. It's probably some type of font issue or something like you said. I know when I get an email on my blackberry from anyone who puts a smiley face it displays it as a J also. I thought it might be a common annoyance to people and thus a quick fix would be available but i guess i'll have to keep looking. Thanks for your help.

EDIT:.. After your suggestion about wingdings font issues.. i found this [http://www.jaanuskase.com/en/2006/02/what_does_j_mean.html]("http://www.jaanuskase.com/en/2006/02/what_does_j_mean.html") on the issue. It appears to be an issue with crappy coding or something with outlook. I tested this by trying to send myself an email with smily faces in it from thunderbird client to a thunderbird client.. and the smiley was perfect.. 

so it's definetly something with outlook I guess. Not sure if there is a way to fix this or not since it's really an issue with the sending persons email client but if anyone has any suggestions let me know. Thanks.

---

### Post by shadowfoxx on 2009-10-27
Looks like this will fix the problem, however, it written for a windows system. Does anyone know how to translate this article into Linux?  [http://www.justinswan.com/damn-js-in-thunderbird-emails-smiley-faces.html]("http://www.justinswan.com/damn-js-in-thunderbird-emails-smiley-faces.html")


I don't know that much about this stuff.. I might just need to install the wingdings font or something.. but I have no idea how.

---

### Post by shadowfoxx on 2009-10-27
I just wanted to add that thanks to QLee I have solved the mystery and am posting it here in the event anyone else wants to use this information. To allow smiley's in thunderbird I did the following:

1) downloaded the wingding.ttf font from [http://www.afosteo.org/Download/Fonts/]("http://www.afosteo.org/Download/Fonts/")
2) I then made a directory by using the following terminal command
            sudo mkdir /usr/share/fonts/truetype/myfonts
3) And finally I copied the font into the newly created directory using this command
            sudo cp [path of winding.ttf] /usr/share/fonts/truetype/myfonts/wingding.ttf


Done! Now all the smiley's in thunderbird show up as smilies not J   :)

*** and just for the record Giblet5 is a douche and was obviously wrong as the only problem was the font ***

---

