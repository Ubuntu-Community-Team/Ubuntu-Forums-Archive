---
title: "How to convert from day of year to year/month/day format"
date: 2012-07-23
forum: General Help
---

### Post by mike_kzc on 2012-07-23
I am trying to convert a dayofyear to year/month/day format, currently, I have to write about 20 Matlab lines to do this. I bet Ubuntu has a better way to do it.

Basically, what I want is: given xth day of 1998 and then convert it to 19980101, 19980102, ... etc., i.e., 1st==> 19980101, 2nd==>19980102 ... 365==> 19981231

Thanks.

Here is the Matlab code I use:

******************
clc
clear

yr=['1998'];mn={'01','02','03','04','05','06','07','08','09','10','11','12'};
dy=[31,28,31,30,31,30,31,31,30,31,30,31];

jsq=0;
ymd{1,365}='0'; %year month day
dayofyear(1,365)=0;
for i=1:12
    for j=1:dy(i)
         jsq=jsq+1;
        tmp=num2str(j);
        if length(tmp)==1
           tmp1=['0',tmp];
        else
           tmp1=tmp;
        end
        tmp2=[yr,char(mn(i)),tmp1];
        ymd{jsq}=tmp2;
        doy(1,jsq)=jsq;
    end
end
***********************

---

### Post by quux on 2012-07-23
On way to achieve this using Python's datetime module:
```

import datetime
print datetime.date(1998,1,1) + datetime.timedelta(31)

```
where 31 is day of year you want to convert.

In case you like omit the dashes, you could use something like:
```

import datetime
d = datetime.date(1998,1,1) + datetime.timedelta(31)
print d.strftime("%Y%m%d")

```

---

### Post by asmoore82 on 2012-07-23
[SIZE="3"]BIG +1[/SIZE] for Python and reaching out to a standard date/time codebase.

I'm not sure if you need it to work for years other than 1998, but what about leap years? Python will take care of that for you too.

You'd also need to rollback the start date by 1. So, for 1998, start with date(1997, 12, 31) and then add your day-of-year number.

---

### Post by Vaphell on 2012-07-23
date command will do it with ease
```
$ y=2012; n=25; date -d "$y-01-01 + $((n-1)) days" +%D
01/25/12
$ y=2012; n=225; date -d "$y-01-01 + $((n-1)) days" +%D
08/12/12
$ y=2012; n=365; date -d "$y-01-01 + $((n-1)) days" +%D
12/30/12
```
date -d is set to 'first day of year $y + (n-1) days' so when y=2012; n=225; the expression becomes
```
date -d "2012-01-01 + 224 days"
```
+%D formats output to USian date format.
date --help for more details.

*date -d "$y-01-01 + $((n-1)) days" +%D* line is highly reusable and can used to create a small script accepting year and day as params
```
#!/bin/bash
y=$1; n=$2
date -d "$y-01-01 + $((n-1)) days" +%D
```

---

### Post by asmoore82 on 2012-07-23
> **Vaphell said:**
> date command will do it with ease
Unless you're using a 32-bit system. You can easily hit the 2038 bug (32-bit overflow) in either direction (past or future)...

```
**$ date -d "1998-1-1 + 59 days"**
Sun Mar  1 00:00:00 EST 1998
**$ date -d "2000-1-1 + 59 days"**
Tue Feb 29 00:00:00 EST 2000
**$ date -d "2037-1-1 + 59 days"**
Sun Mar  1 00:00:00 EST 2037
**$ date -d "2038-1-1 + 59 days"**
[COLOR="Red"]date: invalid date `2038-1-1 + 59 days'[/COLOR]
**$ date -d "1902-1-1 + 59 days"**
Sat Mar  1 00:00:00 EST 1902
**$ date -d "1901-1-1 + 59 days"**
[COLOR="Red"]date: invalid date `1901-1-1 + 59 days'[/COLOR]
```

---

### Post by svalbard on 2012-08-05
There's actually a pretty easy way to do this from MATLAB with the DATENUM and DATESTR functions. For example, the following code prints out the date of the 103rd day in 1998 (which apparently happened to be April 13th) :

```

datestr(datenum(1998,1,0) + 103, 'yyyymmdd')

```Of course, by using Python you gain the ability to run your script from a terminal easily.

---

