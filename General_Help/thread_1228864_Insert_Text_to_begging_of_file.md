---
title: "Insert Text to begging of file?"
date: 2009-08-01
forum: General Help
---

### Post by Chamillionaire2 on 2009-08-01
What's Up?

OK, So I know if i wanted to append something to a new line in a file i would.

echo text >> file.txt

But i need to be able to put a word at the beginning of every line. Is their a way to do that?

Thanks Bye.

---

### Post by sisco311 on 2009-08-01
```
sed -i "1i text" filename
```

---

### Post by Chamillionaire2 on 2009-08-01
> **sisco311 said:**
> ```
sed -i "1i text" filename
```

Thanks, But that moves everything else down to another line.

I have.
```
http://www.www.com/
http://www.www.com/
http://www.www.com/
```

And i want to change it via terminal to.
```
firefox http://www.www.com/
firefox http://www.www.com/
firefox http://www.www.com/
```

Thanks Bye.

---

### Post by kjohri on 2009-08-01
Try,

sed '1,$s/^/firefox /' *filename*

---

### Post by Chamillionaire2 on 2009-08-01
> **kjohri said:**
> Try,

sed '1,$s/^/firefox /' *filename*

Terminal Wizard! [img]http://www.iconarchive.com/icons/icojoy/enjoyment/wizard-48x48.png[/img]

Thanks alot :-)

---

