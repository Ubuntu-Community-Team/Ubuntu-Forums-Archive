---
title: "Table Prefix, Mysql Database name"
date: 2012-02-21
forum: General Help
---

### Post by doctortonic on 2012-02-21
I just installed wordpress and reading tutorial's they all kindly suggest me to change the Table Prefix name.

The default name is wp_ ( two characters and one _ )

I am thinking to change to something like this:

white_glue_city_

or

white_glue-city_

or

white_glue.city_

Is a problem if the database name have 33 characters and I am using . and _ and - and . as separators between words?

---

### Post by TeoBigusGeekus on 2012-02-22
Underscores (_) and dashes (-) are ok; I don't think periods (.) are though.

Mysql uses the period to access databases and tables (Mydatabase.table1, or table1.column5, etc.), just like accessing classes in C++.

I also don't think you'll have problems with long table names.

---

### Post by doctortonic on 2012-02-27
[QUOTE= 1.Unquoted names can consist of any alphanumeric characters in the server's default character set, plus the characters '_' and '$'

says [http://www.informit.com/articles/article.aspx?p=30875](http://www.informit.com/articles/article.aspx?p=30875)

So just stick with _ to seperate your words. [/QUOTE]



______

[http://www.000webhost.com/forum/customer-assistance/28542-table-prefix-mysql-database-name.html](http://www.000webhost.com/forum/customer-assistance/28542-table-prefix-mysql-database-name.html)

______

---

