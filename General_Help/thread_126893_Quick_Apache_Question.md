---
title: "Quick Apache Question"
date: 2006-02-07
forum: General Help
---

### Post by denisesballs on 2006-02-07
If I want my apache server to show it's ip address on a given web page when I visit it, how would I? Either with apache or php would be very helpful. Thanks.

---

### Post by denisesballs on 2006-02-07
Figured it out:

```
<?php
$output = shell_exec('/sbin/ifconfig eth0');
echo "<pre>$output</pre>";
?>
```

---

