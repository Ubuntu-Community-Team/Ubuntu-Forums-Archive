---
title: "give me some advice!"
date: 2010-05-04
forum: General Help
---

### Post by Acceptance on 2010-05-04
hi everyone :)

i'm new in ubuntu.
now i install SugarCRM on ubuntu but it appears two error messages.


**Warning**:  require_once(modules/DynamicFields/DynamicField.php) [[function.require-once]("http://localhost/SugarCE-Full-5.5.1/function.require-once")]: failed to open stream: No such file or directory in **/var/www/SugarCE-Full-5.5.1/data/SugarBean.php** on line **52**

**Fatal error**:  require_once() [[function.require]("http://localhost/SugarCE-Full-5.5.1/function.require")]: Failed opening required 'modules/DynamicFields/DynamicField.php' (include_path='.:/usr/share/php:/usr/share/pear') in **/var/www/SugarCE-Full-5.5.1/data/SugarBean.php** on line [B]52

[/B]Can anybody tell me how could it be ?
thz :)

---

### Post by LifeOnMars on 2010-05-04
You might be better off asking the folks at SugarCRM about this.  It looks like your include path isn't set properly, and that's likely to be in a SugarCRM ini file somewhere.

---

