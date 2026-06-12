---
title: "How To Put Buttons into Websites"
date: 2010-11-08
forum: General Help
---

### Post by chome4 on 2010-11-08
Using Kompozer and need some buttons in a web page but there doesn't seem to be an obvious way of doing this without mastering code?

Any ideas?

---

### Post by howefield on 2010-11-08
Moved to General Help.

---

### Post by Joeb454 on 2010-11-08
I believe all you need to add a button is [html]<input type="button" value="Press Me!" />[/html]

This would generate a button that has the text **Press Me!** on it.

Of course, you should give it a value, and an id or name etc. but that's the basic principle :)

---

### Post by SeijiSensei on 2010-11-08
That will create a button, but it won't do very much.  If you want to create a button to submit a form, use

```
<input type='submit' value='Press Me to Submit'/>
```

That will display "Press Me to Submit" in the button, and clicking it will submit the form data to whatever handles actions for the form.

You can also make buttons that run client-side scripts using the "onclick" attribute.  

I **strongly** suggest you do some reading on HTML itself and not rely solely on WYSIWYG composers.  Even the official documentation from the World Wide Web Consortium isn't that hard to decipher.  For instance, the documentation for forms and form fields like INPUT and BUTTON is [here](http://www.w3.org/TR/1999/REC-html401-19991224/interact/forms.html).  Browsing the HTML tutorial at [w3schools.org](http://www.w3schools.com/html/default.asp) is a good starting point.

---

