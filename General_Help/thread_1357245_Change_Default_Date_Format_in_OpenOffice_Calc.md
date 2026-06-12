---
title: "Change Default Date Format in OpenOffice Calc?"
date: 2009-12-17
forum: General Help
---

### Post by Ubuntist on 2009-12-17
When I type a date into a cell in an OpenOffice.org Calc worksheet, it is formatted as DD/MM/YY by default.  I'd rather have D MMM YY (i.e., "6 Jan 2010") as the default.  Would anyone know how to change the default date format?

---

### Post by Rmantingh on 2009-12-17
I have no problem entering your date format into Calc.
If I type 1 Jan 10 (or 1 jan 2010) it gives me a correct date back.
Admittedly this is then initially converted to the default DD/MM/YY format but this is a display format and can be easily changed by setting the format of the cell:-
Format -> Cells -> Numbers tab -> Date (select one from the list or enter a custom format string)

---

### Post by Ubuntist on 2009-12-17
I get the same behavior: when I type in D MMM YY, it is correctly converted to DD/MM/YY.  That's no problem.  I just wish I could get Calc to use D MMM YY by default, so I wouldn't have to keep changing the format.  Anyway to do that?

---

### Post by mynamewastaken1 on 2010-01-12
[http://openoffice.blogs.com/openoffice/2007/07/correcting-a-sm.html](http://openoffice.blogs.com/openoffice/2007/07/correcting-a-sm.html)

I had the same problem. The link above describes how to fix it. The link changes something else, but the same method will work for what you want. Just select the appropriate date format instead of checking that checkbox. I'm sure you'll figure it out.

---

### Post by Rmantingh on 2010-01-12
I fail to see how this would work (perhaps I'm missing something).
I've tried setting the default style to be Date -> D MMM YY
All this does is that any number entered in any of the cells is automatically converted to a date.
How is that helpful?
If I enter, for instance, the number 1 it changes it to "31 Dec 99".

---

### Post by MathUHenry on 2010-05-11
This doesn't quite work for me. I can correct the date format to YY-MM-DD and save it as the template. But then when I open a document and type a number, it gets forced to a date format. When I set the cells to default to number format (as it should be) then type a date, the date is again defaulting to a wrong format. Is it possible to correct the "Default" date format while still using US English?

---

### Post by MathUHenry on 2010-08-17
I finally figured out how to do this and am going through and posting the solution to the threads I've been reading for help:

1) in spreadsheet press Ctrl F11
2) Default - Modify
3) Date
4) change the language until you find one that defaults to the format you like (you CANNOT specify your own format) I like Uyghur and Zulu
5) click OK - OK
6) File - Templates - Save
7) File - Templates - Organize
8 ) right click the saved template and "Set As Default Template"

When a date is entered, it will now be recognized from the correct format and will be rendered in the correct format.

---

### Post by Ubuntist on 2010-08-22
Thank you MathUHenry!!!

---

### Post by Ubuntist on 2010-09-26
I now have a new problem.  Having changed the default style as suggested, dates appear in the form that I like.  The problem is that all numbers are by default converted to dates.  For example, if I enter "123456" into a cell to which I have applied no format, it becomes "3 Jan 38".

Is there anything I can do about this?

Thanks....

---

### Post by AlanPo on 2010-12-05
> **Ubuntist said:**
> I now have a new problem.  Having changed the default style as suggested, dates appear in the form that I like.  The problem is that all numbers are by default converted to dates.  For example, if I enter "123456" into a cell to which I have applied no format, it becomes "3 Jan 38".

Is there anything I can do about this?

Thanks....


Is there any GUI or something tested where it is possible to change format for date? Systemwide?
editing 
/etc/default/locale
and doing localedef -f UTF-8 -i LV_date LV_date.UTF-8
is not the answer. it leads to errors.
Language reinstall or changin is not the answer too - you change date format and all associated things with language changes also. This is common BUG in all versions of Ubuntu.
And why it should be forbidden to change this small thing for regular user?

---

### Post by Nasher800 on 2012-12-06
I created an account on this forum specifically to THANK MathUHenry for posting a working solution to this problem. 

I'm one of those random people who uses a search engine to try and figure out how to fix things. In this case, I was growing increasingly exasperated by OpenOffice Calc automatically adjusting the date I was entering into a spreadsheet. I kept thinking... WTF is going on? Can't this MF'ing software just KEEP what I'm typing in?! So annoying!

Your instructions proved to be FANTASTIC! 

So... thank you! :)


> **MathUHenry said:**
> I finally figured out how to do this and am going through and posting the solution to the threads I've been reading for help:

1) in spreadsheet press Ctrl F11
2) Default - Modify
3) Date
4) change the language until you find one that defaults to the format you like (you CANNOT specify your own format) I like Uyghur and Zulu
5) click OK - OK
6) File - Templates - Save
7) File - Templates - Organize
8 ) right click the saved template and "Set As Default Template"

When a date is entered, it will now be recognized from the correct format and will be rendered in the correct format.

---

### Post by vanadium on 2012-12-06
> 4) change the language until you find one that defaults to the format you like (you CANNOT specify your own format) 
The date format can be given as a format code (see field "format code"), and thus is pressy customizable: you do not need to take a preset.

---

