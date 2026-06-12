---
title: "Why do php file on my desktop have a flash icon?"
date: 2012-08-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-08-30
they only have this icon on my desktop
if a browse to them in a file browser they don't look like flash icons
```
~$ cat Desktop/index.php 
<pre>
<?php
$list=scandir("/usr/share/cowsay/cows/");
$type=Array("say","think");
echo shell_exec(
    '/usr/games/fortune | /usr/games/cow'.$type[rand(0,1)].' -f "'.substr(
        $list[rand(2,count($list)-1)],
        0,
        -4
    ).'"'
);
?>
</pre>
```

---

### Post by pqwoerituytrueiwoq on 2012-10-01
This is a icon theme issue with the 32 size icon for php files
the workaround is to use 42px icons on the desktop
[http://ubuntuforums.org/showpost.php?p=12271706&postcount=7](http://ubuntuforums.org/showpost.php?p=12271706&postcount=7)

---

