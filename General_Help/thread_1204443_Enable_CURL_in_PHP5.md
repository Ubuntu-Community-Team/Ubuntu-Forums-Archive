---
title: "Enable CURL in PHP5"
date: 2009-07-04
forum: General Help
---

### Post by cpm30 on 2009-07-04
I tried adding extension=php_curl.dll to php.ini and restarted and it still does not work. Any ideas?

---

### Post by wojox on 2009-07-04
What cURL script you running?

Try

[PHP]
<?php
echo '<pre>';
var_dump(curl_version());
echo '</pre>';
?>
[/PHP]

---

