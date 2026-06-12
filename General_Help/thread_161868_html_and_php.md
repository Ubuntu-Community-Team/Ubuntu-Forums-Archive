---
title: "html and php"
date: 2006-04-17
forum: General Help
---

### Post by bunnieofdoom on 2006-04-17
is there a linux native hml to php converter?:)

---

### Post by enopepsoo on 2006-04-17
html and php don't really serve the same purpose.
if you have any php code you can just put it inline in an html file and rename to .php and your apache server should parse it, given that you have the right packages installed.  Something like libapache2-mod-php5.

---

### Post by jazzmuzik on 2006-04-17
Php and html are two different things. Php is a scripting language and html is a markup language. Php is used to make html pages, but I'm not sure what you are trying to do. Maybe a better explanation would help.

---

### Post by jamesdodd on 2006-04-18
I totally agree with what the others have said....


But I would just like to ask: "What is it that your wanting to do?"

I understand that you are wanting to convert a HTML file into a PHP file.

But why?

If you just wanting to use some HTML in a PHP file then you'll probably need to learn more about PHP: [www.w3schools.com/php]("http://www.w3schools.com/php/default.asp")

If you just want all HTML content in a PHP file: Sure you could just rename the file from index.html to index.php or whatever.

But since the web server will parse the PHP file checking for other content it will be slightly slower (not much) so its probably better to just better to keep your file as *.html. Unless your server is configured to parse HTML files as PHP then it just doesn't matter.

Hope that makes sense

---

