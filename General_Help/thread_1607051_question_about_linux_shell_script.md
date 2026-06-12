---
title: "question about linux shell script"
date: 2010-10-27
forum: General Help
---

### Post by oren tal on 2010-10-27
I started to learn script and I have seen the following  script code:
```

function today {
    echo "Today's date is:"
    date +"%A, %B %-d, %Y"
}

```

what I don't understand is the meaning of the %A, %B %-d, %Y?

I need explanation for this ?

Thanks.

---

### Post by KaiO on 2010-10-27
The stuff within the quotation marks defines how the date will be formatted/displayed.

[http://unixhelp.ed.ac.uk/CGI/man-cgi?date](http://unixhelp.ed.ac.uk/CGI/man-cgi?date)

---

### Post by oren tal on 2010-10-27
> **KaiO said:**
> The stuff within the quotation marks defines how the date will be formatted/displayed.

[http://unixhelp.ed.ac.uk/CGI/man-cgi?date](http://unixhelp.ed.ac.uk/CGI/man-cgi?date)

thanks.

---

### Post by linux-hack on 2010-10-27
> **oren tal said:**
> I started to learn script and I have seen the following  script code:
```

function today {
    echo "Today's date is:"
    date +"%A, %B %-d, %Y"
}

```

what I don't understand is the meaning of the %A, %B %-d, %Y?

I need explanation for this ?

Thanks.

they are variables knows by the date command so it knows how you want to output the date (I meen the format)example:

YEAR/MONTH/DAY
or
DAY/MONTH/YEAR

stuff like this.

Hope I explained easily enough

---

