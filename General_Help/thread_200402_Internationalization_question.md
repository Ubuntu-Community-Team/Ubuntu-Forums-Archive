---
title: "Internationalization question"
date: 2006-06-20
forum: General Help
---

### Post by daedalusman on 2006-06-20
I don't really know if this is actually an internationalization problem or not but I was wondering how I could get firefox to display all characters correctly? You can see in my screenshot what I am talking about. Can someone help me on this, thanks.

---

### Post by seshomaru samma on 2006-06-20
[QUOTE=daedalusman]I don't really know if this is actually an internationalization problem or not but I was wondering how I could get firefox to display all characters correctly? You can see in my screenshot what I am talking about. Can someone help me on this, thanks.[/QUOTE]

It appears you need to install some fonts
This never happened to me in Ubuntu , I can always see all languages right after fresh install. But when I installed Fedora I had similar Firefox problems.
Try :
```
sudo apt-get install xfonts-intl-arabic
sudo apt-get install xfonts-intl-asian
sudo apt-get install xfonts-intl-chinese
sudo apt-get install xfonts-intl-chinese-big
sudo apt-get install xfonts-intl-european
sudo apt-get install xfonts-intl-japanese
sudo apt-get install xfonts-intl-japanese-big
sudo apt-get install xfonts-intl-phonetic
sudo apt-get install gsfonts-x11
sudo apt-get install msttcorefonts
sudo fc-cache -f -v
```

---

### Post by yopnono on 2006-06-20
I have the same in dapper and FX. I also see this in windows ver of FX, but it's a pipe character then. (|) This did not happen in the 1.0.x ver of FX.

And it's only if someone use a break in their topic/post/RSS feed

---

### Post by daedalusman on 2006-06-20
Thanks for the replies. It seemed to have gotten rid of some of my problems but I'm still getting some wierd symbols on some pages. Here is a screenshot of this.

---

### Post by bertilow on 2006-06-21
[QUOTE=daedalusman]Thanks for the replies. It seemed to have gotten rid of some of my problems but I'm still getting some wierd symbols on some pages. Here is a screenshot of this.[/QUOTE]

That weird symbol means that the character is wrongly encoded in
the web page. It's so wrong that it doesn't mean anything. There is
no character to display. It's just a mistake - junk.

The actual problem is most probably that the web page is announced
with a different encoding than it actually uses. In that case it might
help to manually switch to another encoding (probably in the menu
"View -> Character encoding").

But if it's a really bad case (maybe several different encodings used
at the same time in the same page - a big no-no), then there is
nothing you can do - except complain to the page author.

---

