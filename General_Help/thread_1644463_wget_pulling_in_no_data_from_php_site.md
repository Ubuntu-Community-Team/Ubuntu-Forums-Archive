---
title: "wget pulling in no data from php site"
date: 2010-12-13
forum: General Help
---

### Post by JL23 on 2010-12-13
Hello, I am trying to download data from my server using wget.

I send the login details and store the cookie. I then rotate through 50  numbers to copy the data into new files. The saved files are always blank  i.e 0kb file size.

My website stores data on individual pages e.g.: (i have changed my actual site name to "mywebsite")
[URL="http://admin.mywebsite.com/index.php/print_view/?html=true&order_id=50"]
[/URL]'http://admin.mywebsite.com/index.php/print_view/?html=true&order_id=50

I am trying to rotate through the numbers 50 to 1 and extract the data from each page. 


The code I am using is below:

#!/usr/bin/perl 

system ("wget --post-data  'username=ghssld&password=ewui394&autologin=1' --cookies=on  --keep-session-cookies --save-cookies=cookie.txt  http://admin.mywebsite.com/index.php/login");

$x = 50;
while ($x <= 1) {
    system ("wget --wait=400 --post-data 'html=true&order_id=50'  --referer=http://admin.mywebsite.com/ --cookies=on  --load-cookies=cookie.txt --keep-session-cookies  --save-cookies=cookie.txt  http://admin.mywebsite.com/index.php/print_view/");
    
    system ("wget --post-data 'html=true&order_id=50'  --referer=http://admin.mywebsite.com/ --cookies=on  --load-cookies=cookie.txt --keep-session-cookies  --save-cookies=cookie.txt  http://admin.mywebsite.com/index.php/print_view?");
$x++;
}


Can anyone help me modify my code so data is pulled correctly and the saved files are not blank? 
Thank you

---

### Post by Interestedinthepenguin on 2011-01-15
Hello.

I have no experience with perl, but have tried my hand at this issue with wget:

Try:
```

wget --cookies=on --save-cookies wget_cookies.txt --keep-session-cookies --post-data=login=yourusername\&passwd=yourpassword http://admin.mywebsite.com/index.php/login 
```

```

wget -E --load-cookies wget_cookies.txt http://admin.mywebsite.com/index.php/print_view/?html=true&order_id={1..50} 
```

"{1..50}" should get pages with the "order_id=" from 1 to 50. If you have pages that count by 50s (50,100,150...) you can try {50,100,150} and so on.

Are you using the actual login fields' names? I think the actual names of the login fields are supposed to be used in place of "username" and "password" in the --post-data entry. View the login page's source and look for the entries "input" that refer to the login fields and use their names in --post-data.

---

