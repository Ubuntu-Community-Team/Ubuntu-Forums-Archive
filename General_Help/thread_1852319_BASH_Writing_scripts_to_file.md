---
title: "BASH Writing scripts to file"
date: 2011-09-29
forum: General Help
---

### Post by hantechbl on 2011-09-29
Hello, I'm trying to make a script that writes components (other scripts) to various files I'm doing it in this format:
```
#!/bin/bash
echo "#!/bin/bash" > file.sh
echo "echo hello" >> file.sh
echo "echo How do I enter variables so they show up as" >> file.sh
echo "echo $variable shows up as $variable instead of blank value?" >> file.sh
```
can anybody tell me how to get that to work? so that it actually says $variable instead of a blank value.

---

### Post by sisco311 on 2011-09-29
Use single quotes or escape the $:
```
echo '$vaiable'
echo "\$variable"

```
See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

