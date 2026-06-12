---
title: "Need help with making a file"
date: 2011-04-19
forum: General Help
---

### Post by Jhegs on 2011-04-19
Ok I am working on a project but it consist of a large amount of numbers. I have tried using OpenOffice to produce this list of numbers but it keeps crashing when I reach a certain point.
 
So I was looking for some help. I need to see if someone could either help me with using a script or program to export these numbers into a .txt file or if someone could just make the list for me.
 
I am looking for a text file that will have the numbers 1000000000 to 9999999999 in order. I understand this is a large amount of numbers but this something I don't have the time to just do manually and each time I try to do it with OpenOffice it crashes around 1009000001.
 
Any help would be much appreciated. 
 
Thanks in advance.
Oh and I need the text file to look like this:
1000000000
1000000001
1000000002
1000000003
.
.
. etc

---

### Post by An Sanct on 2011-04-19
create this bash script

```

#!/bin/bash
for ((x=1000000000; x <= 9999999999; x++)); do
  printf '%3d\n' "$x"
done

```

name it "**script.sh**" and then execute it like **bash ./script.sh>a.txt**

That should do it.

---

### Post by An Sanct on 2011-04-25
Did this solution work for you? If so, please mark the thread as solved under thread tools.

---

