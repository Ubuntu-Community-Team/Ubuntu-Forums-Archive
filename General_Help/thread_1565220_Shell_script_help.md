---
title: "Shell script help"
date: 2010-08-31
forum: General Help
---

### Post by polardude1983 on 2010-08-31
OK so i got a shell script to pull a twitter feed (though it hasn't updated from twitter and i dont know why but it pulls it) ANYways
I was wondering if there is a way i can configure this script so it displays a word in a certain font under each tweet is that possible?

here is my shell script

```
 # RSS Feed Display Script by Hellf[i]re v0.1
#
# This script is designed for most any RSS Feed. As some feeds may not be
# completely compliant, it may need a bit of tweaking
#
# This script depends on curl.
# Gentoo: emerge -av net-misc/curl
# Debian: apt-get install curl
# Homepage: http://curl.haxx.se/
#
# Usage:
# .conkyrc: ${execi [time] /path/to/script/conky-rss.sh}
#
# Usage Example
# ${execi 300 /home/youruser/scripts/conky-rss.sh}

#RSS Setup
URI=http://twiterlist2rss.appspot.com/polardude1983/lists/all/statuses.rss #URI of RSS Feed
LINES=7 #Number of headlines

#Environment Setup
EXEC="/usr/bin/curl -s" #Path to curl

#Work Start
$EXEC $URI | grep title |\
sed -e :a -e 's/<[^>]*>//g;/</N' |\
sed -e 's/[ \t]*//' |\
sed -e 's/\(.*\)/ \1/' |\
sed -e 's/\.//' |\
sed -e 's/\"//' |\
sed -e 's/\"//' |\
head -n $(($LINES + 2)) |\
tail -n $(($LINES))
```

Here is the code in my conky to pull it

```
${voffset 173}${execi 300 /home/christoph/scripts/conky-rss.sh | fold -w66}
```

---

### Post by djyoung4 on 2010-08-31
do you mean you want each tweet to be in a different font?
sidenote: i would post your question on the .conkyrc thread.  You'll probably get more a response there.

---

### Post by polardude1983 on 2010-08-31
I want the letters "D B" to be displayed after every tweet in a different font.

For conkyrc thread i found posts that are tagged with conkyrc but not a conryc forum.

---

### Post by djyoung4 on 2010-08-31
[This thread.]("http://ubuntuforums.org/showthread.php?p=9791334#post9791334")  And I'm still a little confused.  Do you want something like this:
tweet
DB in a certain font
tweet
DB in another font
etc.

---

### Post by polardude1983 on 2010-09-02
> **djyoung4 said:**
> [This thread.]("http://ubuntuforums.org/showthread.php?p=9791334#post9791334")  And I'm still a little confused.  Do you want something like this:
tweet
DB in a certain font
tweet
DB in another font
etc.

Yep that's exactly what i want :D

---

