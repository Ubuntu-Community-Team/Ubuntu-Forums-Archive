---
title: "downlading using terminal"
date: 2011-06-15
forum: General Help
---

### Post by Rakeshvijayan on 2011-06-15
I have a doubt if download any thing using terminal it may be interrupt by power failure etc is it able to posepond the download again ,when it broken ?

---

### Post by nothingspecial on 2011-06-15
Sure you can.

Use wget, for example
```

wget http://www.website.com/file_to_download
```

If it get's interupted start wget again with the -c flag
```

wget -c http://www.website.com/file_to_download
```

and it will start where it left off.

---

### Post by Rakeshvijayan on 2011-06-20
Thanks for the new information let me know  the character  -c indicates

---

