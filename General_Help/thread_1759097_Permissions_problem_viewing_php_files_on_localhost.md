---
title: "Permissions problem viewing php files on localhost"
date: 2011-05-15
forum: General Help
---

### Post by jondiced on 2011-05-15
I'm teaching myself php. Rather than upload my files to my webpage every time I make a change, naturally I would rather just view them while they're still on my computer. I can't seem to configure apache correctly, though.

The DocumentRoot value for apache2 is /var/www/, the default setting. Loading [http://localhost](http://localhost) in a browser works fine, as does loading my test file (foo.php) from that directory. However, once I added a symbolic link in /var/www/ to the folder where I'm developing my php files, I started getting a permissions error:

```
Forbidden

You don't have permission to access /php/ on this server.
Apache/2.2.14 (Ubuntu) Server at localhost Port 80
```

This seems like a pretty entry-level problem, so all my searches only lead to solutions to more complicated issues. Can anyone help?

---

