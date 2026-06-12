---
title: "how to add css to .php file...?"
date: 2009-08-07
forum: General Help
---

### Post by kuldeepsidhu on 2009-08-07
plz give me some php knowledge..i ll be thankful to you..sir.. i have to include css files in my php file...how to do this..i am beginner..so plz tell me step by step..i have files index.php,header.php..i want to change the font color in the header.php file..how to do.it.?

---

### Post by furuno on 2009-08-08
Pretty easy, add this inside your <head></head> tag :
```
<link href="path/to/filename.css" rel="stylesheet" type="text/css" />
```

Example :

```
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <link href="css/mystyle.css" rel="stylesheet" type="text/css"  />  
  <title>My Page</title>
</head>
```

---

### Post by mthalis on 2009-08-08
Vist [http://www.w3schools.com](http://www.w3schools.com) it gives more details with example.

---

