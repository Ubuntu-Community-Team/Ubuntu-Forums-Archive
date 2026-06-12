---
title: "korean (hangul) font support for web sites"
date: 2006-06-14
forum: General Help
---

### Post by stairwayoflight on 2006-06-14
hi,

i installed language-support-ko, but still experience problems viewing web sites with it.

**edit: ** eg. [http://kansuk.or.kr/index.jsp](http://kansuk.or.kr/index.jsp)

is it possible i need win ttf hangul fonts like i installed for english?? where can i get the necessary fonts? stuff still appears as gibberish.

thnks

---

### Post by andraycho on 2006-06-14
It seems the site set its default to english. 

For example, the site should have some like this
<meta http-equiv="Content-Type" content="text/html;charset=euc-kr">
to be encoded as Korean by default.

Anyway you can try in Firefox View->Character Encoding-->More Encodings-->East Asian-->Korean (UHC)

It works for me.

---

### Post by stairwayoflight on 2006-06-16
thnx that worked!

(er 'kamsa hamnida')

---

