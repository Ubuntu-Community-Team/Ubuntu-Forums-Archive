---
title: "Wget several URL's"
date: 2010-05-03
forum: General Help
---

### Post by JakeOfOz on 2010-05-03
Hello, I'm looking for a way to get a lot of internet files automatically using a script with wget. All the files are all categorized to date, and the url is as following:

wget [http: // something. com/somethingsomething/aa/YEAR/aaYYMMDD]("http://www.something.com/somethingsomething/aa/YEAR/aaYYMMDD.gif") (wont work :p)
with the YEAR changing for each year, and the YY for the last to digits of the year, the MM for months and DD for days.

So I produced the following logic:
YY=78
MM=06
DD=19     //startdate

WHILE $YY<=99
wget http://www.something.com/somethingsomething/aa/19$YY/aa&YY$MM$DD.gif
DD=DD+1    //add one day
IF DD>31    //for the end of the month (we'll ignore the short month errors there)
THEN
MM=MM+1   //add one month
DD=01        //reset days
IF MM>12    //end of the year
YY=YY+1    //add a year
MM=01       //reset months

END
END
END

and now the question: how can I get this to work? (running kubuntu by the way)

---

