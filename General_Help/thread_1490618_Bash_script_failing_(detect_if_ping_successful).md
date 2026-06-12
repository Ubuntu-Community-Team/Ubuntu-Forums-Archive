---
title: "Bash script failing (detect if ping successful)"
date: 2010-05-22
forum: General Help
---

### Post by Muscovy on 2010-05-22
I've been making a bash script that involves checking if it can ping. I swear it was working before, but now it throws On or Off depending on if I commend or uncomment the first line here.

The purpose of the while loop is to keep looping until it can successfully ping.

```

#Internet=0
while [ ! $Internet ]
  do
  ping -c 1 -w 3 google.com
  if [ $? -ne  ] ; then
    $Internet = 0
    echo Off
  else
    $Internet = 1
    echo On
  fi
  #More code.
done

```

---

### Post by jamesisin on 2010-05-22
Try setting the first line to Internet= (that's right, nothing).  Then what is the output?

---

### Post by Muscovy on 2010-05-22
The definition isn't skipping the while loop any more, but pings are still always returned as true.

---

### Post by Muscovy on 2010-05-22
Also, I've been getting the following errors.
```

/usr/bin/alexandos-stats: line 7: [: 2: unary operator expected
/usr/bin/alexandos-stats: line 11: =: command not found

```
Which I read up on as "non fatal", and doing the recommended solution of wrapping the problem code in quotes makes it always print Off.

---

### Post by jamesisin on 2010-05-22
I can't make sense of those errors counting your line numbers.  Is that the entire script?

---

### Post by Muscovy on 2010-05-22
Whoops. Found it.
```

  if [ $? -ne **[COLOR="DarkRed"]0[/COLOR]** ] ; then

```
I accidentally deleted the value it was looking for in the returned data from pinging.

---

### Post by jamesisin on 2010-05-22
Doh!  Great news.  Mark your thread as SOLVED.

---

