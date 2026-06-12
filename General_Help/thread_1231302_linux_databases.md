---
title: "linux databases"
date: 2009-08-04
forum: General Help
---

### Post by zippyties on 2009-08-04
the last roadblock I face to a complete migration to ubuntu, is my access 2007 database.

I have been trying to find an equivalent software and so far it seems like the availible programs are at opposite ends of the spectrum.  At one end you have easy to use but limited programs like Kexi and oOo base.  And at the other end you have MSQL and PostgreSQL.  I think I am looking for something in the middle.

So far I have invested time at the lower end of the spectrum with Kexi and oOo Base.  These appealed to me because they don't require programming.  However neither of these will work as they don't output good reports on there own(I realize thier reports are nice but the management at my company would feel they were unacceptable).

I am tentatively eyeing a combination of PostgreSQL and Glade.  But I have absolutely no idea how to implement this, that and I am not a programmer, and don't have more than a few hours a week to learn programming.  Am I barking up the wrong tree here?

---

### Post by mohnkern on 2009-08-04
Have you tried firebird?

> **zippyties said:**
> the last roadblock I face to a complete migration to ubuntu, is my access 2007 database.

I have been trying to find an equivalent software and so far it seems like the availible programs are at opposite ends of the spectrum.  At one end you have easy to use but limited programs like Kexi and oOo base.  And at the other end you have MSQL and PostgreSQL.  I think I am looking for something in the middle.

So far I have invested time at the lower end of the spectrum with Kexi and oOo Base.  These appealed to me because they don't require programming.  However neither of these will work as they don't output good reports on there own(I realize thier reports are nice but the management at my company would feel they were unacceptable).

I am tentatively eyeing a combination of PostgreSQL and Glade.  But I have absolutely no idea how to implement this, that and I am not a programmer, and don't have more than a few hours a week to learn programming.  Am I barking up the wrong tree here?

---

### Post by wojox on 2009-08-04
MySQL really isn't that hard to learn if you have some experience with access. You can download it from the repos and it will install itself. w3m schools has a good beginners guide to start off with.

---

### Post by cariboo on 2009-08-04
You can connect to an Access database using an ODBC connector. Have a look at this [page]("http://www.easysoft.com/developer/interfaces/odbc/linux.html") for info on how it works.

---

### Post by zippyties on 2009-08-04
**@wojox** and **@mohnkern** Thanks for the replys.  It looks like Firebird and MySQL both have a server/client configuration.  Is it possible to double click you database file, and have the computer execute it without having to start or connect to a server(similar to access)? 

**@cariboo907** I have to admit that implementing this solution looks somewhat complicated.  However nothing is impossible, I do have a few questions though, before I invest a lot of effort here.  Will this work with access 2007 databases?  How do I go about doing this?  would I use a program like oOo dbase to connect to the database?  how would it handle the forms/macros and the like which are specific to Access? 

Thanks again,

---

