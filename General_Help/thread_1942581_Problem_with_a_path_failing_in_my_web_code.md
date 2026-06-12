---
title: "Problem with a path failing in my web code"
date: 2012-03-17
forum: General Help
---

### Post by Zewtastic on 2012-03-17
Is it possible to reference a file in another web directory under /var?

I am trying to reference images from one web site into another.

for example:
/var/www/website1/images/tom.jpg

/var/www/website2/show_image.html

where in show_image.html I use: 
src='/var/www/website1/images/tom.jpg'

It does not want to work, driving me crazy. Is it possible? Is it s permissions thing? All have the same permissions.

---

### Post by wojox on 2012-03-17
Use the web address:
```
http://www.something.org/images/tom.jpg
```

---

### Post by Zewtastic on 2012-03-17
I'm writing a lot of PHP code and that solution is not really a solution.

I was really looking for an answer to the question, why does it not work.

---

### Post by jquis8411 on 2012-03-17
The question is confusing. What are you trying to do?  because,  the last post made the most sense.

---

### Post by wojox on 2012-03-17
> **Zewtastic said:**
> I'm writing a lot of PHP code and that solution is not really a solution.

I was really looking for an answer to the question, why does it not work.

```
src="../images/tom.jpg"
```

Picture file resides in the pic directory in a previous directory

---

### Post by Zewtastic on 2012-03-17
It is difficult to explain, I agree.

If you are familiar with creating websites under Ubuntu, they are typically created in the directory

/var/www/

so if you had two websites, green.com and blue.com, there respective directory paths would be

/var/www/green.com
/var/www/blue.com

typically when you write html/code, in my case I write php, you reference files within your websites directory.

I am writing code from inside blue.com, where I want to reference files (in some cases images) in the green.com directory.

So for example in my blue.com website scripts, if I want to display an image that is actually located in the green.com directory, you could directly reference it with:

/var/www/green.com/imagename.jpg

here is the html:
<img src="/var/www/green.com/imagename.jpg" alt="" />

But, for some reason this fails.

---

### Post by Zewtastic on 2012-03-17
> **wojox said:**
> ```
src="../images/tom.jpg"
```

Picture file resides in the pic directory in a previous directory

Yes, I tried this, and it fails. That is why I am posting here, to see if anyone has the same issue or knows why I am having problems.

---

### Post by jquis8411 on 2012-03-17
I see what you are saying. The www directory resides in  var of the host but you do not reference the var directory while making your src referance. if you wanted to find the image you want using the url bar in a browser and enter http:// [www.sitethathasimage/imageyouwant](www.sitethathasimage/imageyouwant) use the same url when writing your markup. 
 So instead of writing src='/var/www/website1/images/tom.jpg' write src=http:[www.website1/images/tom.jpg](www.website1/images/tom.jpg).

---

