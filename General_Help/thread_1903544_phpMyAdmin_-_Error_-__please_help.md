---
title: "phpMyAdmin - Error -  please help"
date: 2012-01-02
forum: General Help
---

### Post by davidtheo on 2012-01-02
Can someone please help me.

I installed wine and then toad,
I tried to run toad but it did not work.
so I restarted my computer and toad still did not work.

I uninstalled toad 

but now when I try to log into phpmyadmin I am getting this error

```
**phpMyAdmin - Error**

 Cannot start session without errors, please check errors given in  your PHP and/or webserver log file and configure your PHP installation  properly.

```I have tried looking for my error_log for php but I can not find it.
I looked on the php.ini and I even uncommented the error_log == error_log.log in php.ini.

I also tried doing

```

find -type f -name error_log

```but this did not return any results

I even tried uninstalling phpmyadmin and reinstalling it but this did not work.

This was working before I installed wine and toad, can anyone please help me.
and php seems to me working fine.

I am using ubuntu 11.10

---

### Post by fdrake on 2012-01-02
can you try this:
```

sudo chmod -R 777 /var/www

```

---

### Post by davidtheo on 2012-01-05
> **fdrake said:**
> can you try this:
```

sudo chmod -R 777 /var/www

```


Hi fdrake

Thanks for this, Sorry I have not gotten back to you sooner but been busy with work :).

Anyway I was going to do this last night but when I when to the DB with phpmyadmin it worked, so not sure what happened.

Thanks anyways

David

---

