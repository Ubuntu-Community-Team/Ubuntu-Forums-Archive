---
title: "save file as ISO 8859, French?"
date: 2011-09-04
forum: General Help
---

### Post by qwertyjjj on 2011-09-04
I am trying to save this file as ISO 8859 so that the French characters work but it keeps saying there are disallowed characters and it won;t save.

Any ideas what is disallowed? Also, when I paste it into an editor it cuts it off at the first backslash \
I get this error:
iconv --from-code=UTF-8 --to-code=ISO-8859-1 english2.php > newfile.php
**iconv: illegal input sequence at position 266**
j@j-Inspiron-9300:~/Desktop/PP$

```

<?php
/*
  $Id: $

  osCommerce, Open Source E-Commerce Solutions
  http://www.oscommerce.com

  Copyright (c) 2007 osCommerce

  Released under the GNU General Public License
*/

define('TEXT_MAIN', '
<hr>
<b style="color: rgb(7,75,138);">
Proxy vous offre l\&#8217;accès à des serveurs proxy et réseau privé virtuel (VPN) pour une grande variété d&#8217;utilisations telles que :<br />
<br />
- accès sécurisé<br />
- navigation sur internet<br />
- navigation anonyme<br />
- visualisation de vidéos<br />
- etc.<br />
<br />
Et ce, à partir de partout dans le monde, grâce à une adresse IP française.<br />

```

---

