---
title: "http://localhost gives errors"
date: 2009-07-09
forum: General Help
---

### Post by biebo on 2009-07-09
when i type [http://localhost](http://localhost)  or [http://localhost/phpmyadmin](http://localhost/phpmyadmin) in my browser it gives errors ,
but it doesnot give errors in [http://localhost/testphp.php](http://localhost/testphp.php).

the error is 
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias([http://localhost/](http://localhost/))
7:getEngineByAlias([http://localhost/](http://localhost/))
8:getShortcutOrURI([http://localhost/](http://localhost/),[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent])



please help me find the problem

---

### Post by biebo on 2009-07-09
Now I can not even open 
[http://mpjexpress.blogspot.com/](http://mpjexpress.blogspot.com/)

a simple site

---

### Post by biebo on 2009-07-09
also 
[www.orkut.com](www.orkut.com) not opening, the same error pops out

---

### Post by cariboo on 2009-07-09
You may have a corrupted browser profile. To check, move your ~/.mozilla to ~/.mozilla.bak, restart Firefox and check to see if you get the same errors. Open an Applications-->Accessories-->Terminal and type:

```
mv ~/.mozilla ~/.mozilla.bak
```

If everything works properly you can import your bookmarks and reinstall the addons.

---

### Post by biebo on 2009-07-10
its now working i restated the system.

but  [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
doesn't work even if i have installed the phpmyadmin

---

### Post by Psyphre on 2009-07-10
I too have a similar problem as the thread starter.

[http://localhost](http://localhost)   <--- works
[http://localhost/testphp.php](http://localhost/testphp.php)  <----works
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)    <----doesnt work

Followed this guide:
[http://info123.org/component/content/article/72-lamp-server-in-ubuntu-jaunty](http://info123.org/component/content/article/72-lamp-server-in-ubuntu-jaunty)

---

### Post by alien8tive on 2009-07-10
In your apache2.conf (if you have apache2 installed), add the line

Include /etc/phpmyadmin/apache.conf

then 

type

sudo /etc/init.d/apache2 restart

Try to go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) again.

---

### Post by Psyphre on 2009-07-10
that worked! thanks

---

### Post by biebo on 2009-07-11
i downloaded phpmyadmin and ectracted to /var/www/phpmyadmin

now it works

---

