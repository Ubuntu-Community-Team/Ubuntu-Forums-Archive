---
title: "bash: list contents of folders"
date: 2011-01-02
forum: General Help
---

### Post by geo909 on 2011-01-02
Hello all,

Could somebody please explain to me how I sould do the following?

I have a folder called "Downloads" and among its contents there are a bunch of files with "flv" extension.

If I do 
```
ls path/to/Downloads/*flv
```

I will get something like this:

```

path/to/Downloads/file1.flv
path/to/Downloads/file2.flv

etc...

```

Is there a way to list the contents of Downloads as
```

file1.flv
file2.flv

etc..

```

without navigating to the "Downloads" folder?

(The reason I want something like that has to do 
with a small script I'm trying to write).

Many thanks in advance.

---

### Post by TeoBigusGeekus on 2011-01-02
```
#!/bin/bash 
for i in $(ls /path/to/folder/*flv) 
do 
fn=$(basename $i) 
echo $fn
done
```

&#922;&#945;&#955;&#942; &#967;&#961;&#959;&#957;&#953;&#940; &#954;&#961;&#953;&#964;&#953;&#954;&#940;&#964;&#963;&#953;...:p

---

### Post by geo909 on 2011-01-02
&#917;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; &#963;&#959;&#953;, &#963;&#973;&#957;&#964;&#949;&#954;&#957;&#949;, &#954;&#945;&#953; &#963;&#949; &#963;&#941;&#957;&#945;!

---

