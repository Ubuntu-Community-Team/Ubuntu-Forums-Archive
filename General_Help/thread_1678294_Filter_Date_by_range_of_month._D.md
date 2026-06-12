---
title: "Filter Date by range of month. :D"
date: 2011-01-30
forum: General Help
---

### Post by Jovenrp on 2011-01-30
Hello!, Can anyone help me on how to filter Date in terminal? I can filter a month from another month using grep but I cant grep multiple months. example, I want to show the data from 20/Jan/2011 to 10/Sep/2011. Grep can only show data of January and September. Is there any other unix commands I can use to achieve what I want? Any help is greatly appreciated. :D :)

---

### Post by Vaphell on 2011-01-30
> I can filter a month from another month using grep but I cant grep multiple months

yes you can
```

grep -E 'Jan|Feb|Mar|Apr|May|Jun'
```

either way grep is not the best way to deal with date ranges. Where do you get data from, in what format and what you want to do with it exactly?

---

### Post by asmoore82 on 2011-01-30
you can also specify multiple match patterns to `grep` ...
```
grep -e "Jan" -e "Feb" -e "Mar"
```

---

### Post by Jovenrp on 2011-01-30
Thanks for the reply, My data comes from a text file, its actually a log of my squid proxy, "access.log" and I am developing a php webpage that shows the access.log in the webpage I am making, The dates I am going to filter came from the webpage which has only 2 inputs, Startdate and Enddate, I want to grep data from startdate and enddate, and in between the startdate and enddate, example. Startdate is January, and the Enddate is September, The data which will be shown is from January to September.

Thanks again. :D

---

### Post by Jovenrp on 2011-01-30
btw, the format of the date is day/month/year

example : 05/Jan/2011

Thanks. :D

---

### Post by Habitual on 2011-01-30
[http://www.cyberciti.biz/faq/sed-display-text/](http://www.cyberciti.biz/faq/sed-display-text/)

---

### Post by Jovenrp on 2011-01-30
Thanks. But I cant use sed to the format of the date I am using which is 30/Jan/2011 to 30/Mar/2011.

cat /var/log/squid/access.log | sed -n '/30/Jan/2011/,/28/Feb/2011/p' 

There is an error which is:


sed: -e expression #1, char 5: unknown command: `J'

Thanks anyway... :D

---

### Post by Jovenrp on 2011-01-30
Thanks. But I cant use sed to the format of the date I am using which is 30/Jan/2011 to 30/Mar/2011.

cat /var/log/squid/access.log | sed -n '/30/Jan/2011/,/28/Feb/2011/p' 

There is an error which is:


sed: -e expression #1, char 5: unknown command: `J'

Thanks anyway... :D

---

### Post by Vaphell on 2011-01-31
```

#!/bin/bash

Jan=01; Feb=02; Mar=03; Apr=04; May=05; Jun=06; Jul=07; Aug=08; Sep=09; Oct=10; Nov=11; Dec=12;

# 2 arguments: 'from' and 'to' in 1999-12-31 format

from=$( echo "$1" | sed -r 's:[^0-9]+:/:g' )
to=$( echo "$2" | sed -r 's:[^0-9]+:/:g' )

echo from $from to $to

while read line
do
  date=$( echo "$line" | sed -r 's:.*([0-9]{2}/[a-zA-Z]{3}/[0-9]{4}).*:\1:g' )
  month=$( echo "$date" | sed 's:[0-9/]*::g' )
  m_num=$(eval "echo \$$month" )
  date=$( echo "$date" | sed -r 's:[a-zA-Z]{3}:'$m_num':g' | awk 'BEGIN { FS="/"; OFS="/" }; { print $3,$2,$1 }' )

  if [ "$date" \< "$to" -o "$date" == "$to" ] && [ "$date" \> "$from" -o "$date" == "$from" ]
  then
    echo $line
  fi
done < /var/log/squid/access.log

```

may be a bit slow - i haven't tested it on a big file. It converts date strings left and right to 'year(4)/month(2)/day(2) all numbers' format, because testing in such scenario is simple - alphabetical order of "2001/12/31" and "2002/01/01" matches natural order of days. Script accepts 2 dates as parameters, 'from' and 'to' in year month day format (any non-digit is replaced by / to normalize format, so you can separate with any non-digit char and it will work). Validity is not checked - if you put 2011-99-55 it won't complain.

```
script 2010-12-12 2011/04/01
```


knowing that logs are usually in chronological order some optimization is possible - if the line does not match the range but the last line did then you can exit the script without checking remaining lines because there is no way they can start matching the range again.
I'll think about other ways to optimize - does the date occupy a fixed position in a log line?

---

### Post by Vaphell on 2011-01-31
newer version, assumes chronological order to exit before end of file, sed and awk dropped from date manipulation, comparison is made on integers (date YYYY/MM/DD -> YYYYMMDD) to simplify conditions even more.
```

#!/bin/bash

start_time=$(date +%s)
Jan=01; Feb=02; Mar=03; Apr=04; May=05; Jun=06; Jul=07; Aug=08; Sep=09; Oct=10; Nov=11; Dec=12;

echo From $( echo "$1" | sed -r 's:[^0-9]+:/:g' ) to $( echo "$2" | sed -r 's:[^0-9]+:/:g' )
from=$( echo "$1" | sed -r 's:[^0-9]+::g' )
to=$( echo "$2" | sed -r 's:[^0-9]+::g' )
found_any=false

while read line
do
  date=$( echo "$line" | sed -r 's:.*([0-9]{2}/[a-zA-Z]{3}/[0-9]{4}).*:\1:g' )
  year=${date:7:4}
  month=$( eval "echo \$${date:3:3}" )
  day=${date:0:2}
  date=$year$month$day
  if (( $date <= $to ))  && (( $date" >= "$from ))
  then
    echo $line
    found_any=true
  else
    if $found_any; then break; fi
  fi
done < /var/log/squid/access.log

finish_time=$(date +%s)
echo "Duration: $((finish_time - start_time)) secs."

```

---

### Post by Jovenrp on 2011-01-31
Thanks for the reply, I'll try your code after I understood all of it, I am having a hard time understanding your code.

this is my php code with a shellscript.

$date = $_REQUEST['date'];

$out = @shell_exec("cat /var/log/squid/access.log | grep '".$date."' | awk '{print $2}' ");

echo $out."<br>";


Yes, The date has a fixed format, "13/Jan/2011".

---

### Post by Jovenrp on 2011-01-31
THANKS!!! I tried your shell script, however, I cant convert it to use the format that I need which is 20/Jan/2011 "dd/Mon/yyyy"... :(

---

### Post by Vaphell on 2011-01-31
i am not sure i get what you mean
doensn't it work or do you want parameters in a 00/Xxx/0000 format?

EDIT:

```

#!/bin/bash

start_time=$(date +%s)
Jan=01; Feb=02; Mar=03; Apr=04; May=05; Jun=06; Jul=07; Aug=08; Sep=09; Oct=10; Nov=11; Dec=12;

echo From $1 to $2
# script parameters ${1} and ${2} in 00/Xxx/0000 format
# year = 4 chars starting at 7 (indexing from 0)
# month = 3 chars starting at 3, substituted by appropriate month number eg 'Jun' -> $Jun = 06
# day = 2 chars starting at 0
from=${1:7:4}$( eval "echo \$${1:3:3}" )${1:0:2}  # date 'from' as integer in YYYYMMDD format
to=${2:7:4}$( eval "echo \$${2:3:3}" )${2:0:2}    # date 'to' as integer in YYYYMMDD format

found_any=false

while read line
do
  logdate=$( echo "$line" | sed -r 's:.*([0-9]{2}/[a-zA-Z]{3}/[0-9]{4}).*:\1:g' )
  date=${logdate:7:4}$( eval "echo \$${logdate:3:3}" )${logdate:0:2} # date as integer in YYYYMMDD format

  if (( $date <= $to ))  && (( $date >= $from ))  # check if date in range
  then
    echo "$line"
    found_any=true
  else
    if $found_any
    then
      break   #leave while loop, dates used to be in range, now they are not
    fi
  fi
done < /var/log/squid/access.log

finish_time=$(date +%s)
echo "Duration: $((finish_time - start_time)) secs."

```
simplified, format of parameters (00/Xxx/0000), comments added

not that i know anything about php, but something like this should do the trick
[php]
$out = @shell_exec(" /path/to/script $datefrom $dateto ");[/php]

---

### Post by Jovenrp on 2011-01-31
THANKS A LOT!!! I adjusted my php code to use your script. Thanks. :D

---

### Post by Vaphell on 2011-01-31
but does it work? :-) if so, could you mark the thread as solved so others with similar problem have it easier to find it.

---

### Post by Jovenrp on 2011-02-01
yes. It work as what I wanted it. :D

---

