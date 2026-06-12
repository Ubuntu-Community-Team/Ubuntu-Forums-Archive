---
title: "how to stop apache2"
date: 2011-05-16
forum: General Help
---

### Post by jnorthr on 2011-05-16
looking to use cherokee as a web server in place of apache2.

can anyone please advise as to how i can disable apache2 startup at boot time ?  will then need to install a script(?) or something to start cherokee at boot time.  

I have read this whole process has something to do with /etc/init.d  scripts but do not know enough to know how to change them. Any ideas this sunny morning ?
):P

---

### Post by sj1410 on 2011-05-16
rcconf is fantastic Runlevel configuration tool similar to ntsysv in redhat

```

sudo apt-get install rcconf
sudo rcconf


```

---

### Post by jnorthr on 2011-05-16
ok, thanx for that - will look into the rcconf idea next. First i'll reload the cherokee server from this blog [http://jnorthr.wordpress.com/wp-admin/post.php?post=66&action=edit]("http://jnorthr.wordpress.com/wp-admin/post.php?post=66&action=edit")

---

