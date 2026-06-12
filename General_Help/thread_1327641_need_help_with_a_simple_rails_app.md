---
title: "need help with a simple rails app"
date: 2009-11-15
forum: General Help
---

### Post by skullsk8er on 2009-11-15
hello guys,

i ran in some trouble just now, and i sure hope that someone doesn't have a thing to do than help the ones in need, or if they do and they would like to help me, I'll do anything...don't get any cute ideas :D
So i have rails version 2.3.4, Ruby version 1.8.7 (2008-08-11 patchlevel 72) [i486-linux], sqlite 3.6.10 , thought it might help.
It's my first pls-pls-help me post so..i don't know how should i do it.I thought it would be best to attach the files that i think are in trouble, as well as anotherone with the error message that i am receiving.
So this is my problem :
1)according to my documentation find_by_sql(sql) : "Executes a custom SQL query against your database and returns all the results. The results will be returned as an array with columns requested encapsulated as attributes of the model you call this method from. If you call Product.find_by_sql then the results will be returned in a Product object with the attributes you specified in the SQL query. "
2)So when i do @products = Product.find_by_sql("SELECT image_url, title, author, price FROM products ORDER BY author") in my controller code, it should give me my 4 objects with the attributes:image_url, title, author, price.
However the browser gives me an error that i can't understand..(it's my first rails everything:app, bugs, debuger, etc etc)
So pls go easy on a ubuntu noob, a rails noob, and a ruby noob..
If u need any support from me let me know pls.

A billion thx in advance,
radu

---

