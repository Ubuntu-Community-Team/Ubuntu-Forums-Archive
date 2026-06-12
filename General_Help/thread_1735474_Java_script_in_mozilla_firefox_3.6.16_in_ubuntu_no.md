---
title: "Java script in mozilla firefox 3.6.16 in ubuntu not working"
date: 2011-04-21
forum: General Help
---

### Post by unloki9 on 2011-04-21
Im currently using Ubuntu 10.04 and I tried programming java scripts in my mozilla, but it's not woking =.=

the content of my java script is:

```

<html>
<body bgcolor=”WHITE”>
<p>Paragraph 1</p>
<script type=”text/javascript”>
document.bgColor = “RED”;
</script>
</body>
</html>

```and I just get this image:

[IMG]http://i1087.photobucket.com/albums/j468/appealinganthony/Screenshot.png[/IMG]

---

### Post by SavageWolf on 2011-04-21
document.bgcolor I think has to be a hexadecimal colour code thing, such as "#ff0000".

[http://html-color-codes.com/](http://html-color-codes.com/)

Failing that, try ```
document.getElementsByTagName("body")[0].style.backgroundColor = "#ff0000";
```

---

### Post by luigi_mb on 2011-04-21
> **unloki9 said:**
> Im currently using Ubuntu 10.04 and I tried programming java scripts in my mozilla, but it's not woking =.=

the content of my java script is:

```

<html>
<body bgcolor=”WHITE”>
<p>Paragraph 1</p>
<script type=”text/javascript”>
document.bgColor = “RED”;
</script>
</body>
</html>

```



The quotation marks "" used may be a problem. I replaced them with the default "" in nedit, and the page displays properly.


/luigi

---

### Post by unloki9 on 2011-04-22
Nyahaha! yes you're right thanks so much! it's working now ^^.. do you know by chance how to make java scripts in netbeans 6.8?

---

### Post by luigi_mb on 2011-04-22
Sorry, I don't use netbeans.

/luigi

---

