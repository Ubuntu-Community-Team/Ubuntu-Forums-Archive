---
title: "Appending files together"
date: 2011-05-23
forum: General Help
---

### Post by hojjat on 2011-05-23
In a directory containing files like:

as12-01
as12-02
be15-01
be15-03
be15-04
...

I want to append all files based on their prefix and create gigantic files (like as12-appended, be15-appended, etc) which contain the complete text of all those files together. If possible, I'd like to separate the content inside the mega-file too, such as:

```

as12-01
blah blah blah
---
as12-02
blah blah blah

```

I have python installed, so a bash or a python solution would be equally ideal

---

### Post by carson1 on 2011-05-23
You should be able to simply do:

cat file1 file2 file3 > output_file

---

### Post by hojjat on 2011-05-23
Simple yet effective! Thank you. I was thinking if there's a way to also implement the separation idea within your solution.

---

### Post by carson1 on 2011-05-23
The simple way would be with a bash script:

#!/bin/bash

cat file1 > output
echo --- >> output
cat file2 >> output
echo --- >> output
cat file3 >> output
echo --- >> output

---

### Post by enimeizoo on 2011-05-23
If you don't want a script, you could try
```
more file1 file2 file3 > output.txt
```This way, the separator is chosen by more, thought. It looks like :
```

::::::::::::::
file1name
::::::::::::::
file1content
::::::::::::::
file2name
::::::::::::::
etc...

```

---

### Post by hojjat on 2011-05-23
Both excellent solutions. I am tempted to learn more about bash programming? Any "for dummies" tutorials you would suggest?

---

