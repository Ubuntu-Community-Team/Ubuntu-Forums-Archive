---
title: "Google calendar supports Konqueror?"
date: 2006-04-13
forum: General Help
---

### Post by ltmon on 2006-04-13
[http://calendar.google.com](http://calendar.google.com) seems to have just launched.  Those of you with a gmail account should be able to check it out.

In any case, I looked at the code and noticed the following snippet:

```

  var a = navigator.userAgent.toLowerCase();
  var i6 = (a.indexOf("msie 6.")!=-1);
  var i = (a.indexOf('msie')!=-1);
  var k = (a.indexOf('konqueror')!=-1);
  var s = (a.indexOf('safari') != -1) || (a.indexOf('konqueror') != -1);
  var n = !i && !s && (a.indexOf('mozilla') != -1);
  var o = !!window.opera;

```

It seems that Konqueror has joined IE, Firefox, Safari and Opera in the list of supported browsers :)

Cheers,

L.

---

### Post by ijanos on 2006-04-13
Sorry, but this snippet means nothing. 
Only IE and FF is officially supported. Again :(

ps: I did a quick test with konqueror and it seems to be working...
pps: Acctually works better than Opera8 but far from perfect :(

---

### Post by ltmon on 2006-04-13
Yeah.. I just tried it at home on Konq (I first posted from work using Firefox).  Too bad :(

It does seem to be usable with Konqueror, but far from perfect.  It's a much nicer experience in Firefox.

L.

---

### Post by Maelgwyn on 2006-04-13
It doesn't seem to like Epiphany much either... Worked, but was very slow!

---

### Post by Video Toaster on 2006-04-13
[QUOTE=Maelgwyn]It doesn't seem to like Epiphany much either... Worked, but was very slow![/QUOTE]
Really?  Epiphany should work the same as Firefox, since they both use Gecko to render the page.  (I haven't actually tried it, though... just stating what SHOULD be :D)

---

