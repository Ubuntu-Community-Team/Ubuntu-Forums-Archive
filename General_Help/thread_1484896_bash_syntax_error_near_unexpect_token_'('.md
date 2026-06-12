---
title: "bash: syntax error near unexpect token '('"
date: 2010-05-16
forum: General Help
---

### Post by Ghasemzadeh on 2010-05-16
I install nfs-common,nfs-kernel-server
Now I can not use
[PHP]
# \home 192.168.1.10(ro,no_root_squash)
[/PHP]
I get
> bash: syntax error near unexpected token `('
when I want to share a folder

---

### Post by gmargo on 2010-05-16
[COLOR=#000000][COLOR=#ff8000][COLOR=Black]> 
# \home 192.168.1.10(ro,no_root_squash) 
[/COLOR][/COLOR][/COLOR]The export specification belongs in /etc/exports; it is not a shell script (and Unix uses forward slashes, not backslashes.)

So edit **/etc/exports** to add:
```

[COLOR=#000000][COLOR=#ff8000][COLOR=Black]/home 192.168.1.10(ro,no_root_squash)  
[/COLOR][/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#ff8000][COLOR=Black]Then run "exportfs -a".  Now you should be able to NFS-mount the directory from that .10 system.
[/COLOR][/COLOR][/COLOR]

---

### Post by Ghasemzadeh on 2010-05-16
Problem solved!

Thanks

---

