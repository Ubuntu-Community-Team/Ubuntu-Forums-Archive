---
title: "PHP Help"
date: 2009-07-28
forum: General Help
---

### Post by mthalis on 2009-07-28
I pass data one page(test.php) to other page(index.php) using **urlencode**

```

header("Location:". BASE_SSL_PATH."login/index.php?error=",urlencode($errmsg1));
```

I want to print that pass value  
```

$a = $_GET['error'];
echo urldecode($a);

```

I try above way but not working how can I fix it, please help me.

note - I did this without urlencode and urldecode

---

### Post by DaithiF on 2009-07-28
Hi, you have a comma before the urlencode, shouldn't it be a period for string concatenation instead.

---

### Post by mthalis on 2009-07-28
Thanks lot,it works now

---

### Post by mthalis on 2009-07-28
If I use this way, Is it secure my data or not? need suggestion

---

### Post by DaithiF on 2009-07-28
> **mthalis said:**
> If I use this way, Is it secure my data or not? need suggestion

if you are asking whether the urlencode-ing of your get parameter makes the passsing of that get parameter secure, then no.  Urlencode just allows strings to be passed safely as part of a url by translating non-alphabetical characters into a url-friendly form.  Its not any kind of encryption.

---

### Post by mthalis on 2009-07-28
So please tell me how I pass data secularly satisfying my requirement(any reference site).

---

### Post by DaithiF on 2009-07-28
is your webserver configured to use SSL, ie does it do https connections?  If so and your PHP app is being accessed via https links then you're probably ok, all traffic to and from your php app should be encrypted, and 3rd parties cannot (easily) intercept and decode the traffic.

If not (ie. if you app is running without SSL, via http links), then you need to do some googling on apache2 + SSL setup, there are plenty of how-to guides available.

---

### Post by mthalis on 2009-07-28
except ssl option other way to pass data?

---

