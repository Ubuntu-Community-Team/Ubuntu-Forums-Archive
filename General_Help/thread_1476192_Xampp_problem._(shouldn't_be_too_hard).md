---
title: "Xampp problem. (shouldn't be too hard)"
date: 2010-05-07
forum: General Help
---

### Post by Logan513 on 2010-05-07
Well, I just installed Xampp into /opt and copied my files that I had made on Windows that I had tested with the Windows version of Xampp. They had worked perfectly on Windows but when I try to open them via Linux I get:

```
**Warning**:  Unknown: failed to open stream: Permission denied in **Unknown** on line **0**

**Fatal error**:  Unknown: Failed opening required '/opt/lampp/htdocs/web_junkie/index.php' (include_path='.:/opt/lampp/lib/php') in **Unknown** on line **0**
```Now here's the PHP (VERY SIMPLE);

```
<?php 
 
$index = "<html> 
<head><title>Web Junkie - Web design service</title></head> 
<body background='img/bg.jpg' text='#FFFFFF' link='FFFF00' vlink='FFFF00' alink='FFFFFF'> 
<table width='60%' align='center'> 
       <tr> 
           <td> 
           <a href='index.php'><img src='img/logo.png' border='0'></a> 
           </td> 
       </tr> 
       <tr> 
           <td><br> 
               <table width='100%' bgcolor='#000000' border='1'> 
               <font face='courier new' color='white'> 
                     <tr align='center'> 
                         <td colspan='2'> 
                         <a href='index.php'>Home</a> | <a href='portfolio.php'>Portfolio</a> | <a href='pricing.php'>Pricing</a> | <a href='contact.php'>Contact us</a> 
                         </td> 
                     </tr> 
                     <tr> 
                         <td width='50%' valign='top'> 
                         The Internet is like a giant brick wall. And each and every website is a graffiti tag. What makes your tag stand out? 
                         At <i>Web Junkie</i> we can help you make your website stand out for a very afordable price. 
                         <hr size='1' color='FF0000'> 
                         But we offer more than just a simple HTML document. We also offer websites with PHP support! 
                         <hr size='1' color='FF0000'> 
                         Go check out our <a href='portfolio.php'>portfolio</a> to see some of the amazing sites by <i>Web Junkie</i>! 
                         </td> 
                         <td align='right'> 
                         <img src='img/graffiti.jpg' border='0'> 
                         </td> 
                     </tr> 
                     <tr> 
                         <td colspan='2'> 
                         <div align='right'> 
                         Sight maintained by <i>Web Junkie</i> © 2010 
                         </div> 
                         </td> 
                     </tr> 
               </font> 
               </table> 
           </td> 
       </tr> 
</table> 
</body> 
</html>"; 
 
echo "$index"; 
 
?>
```But when I go to normal old localhost it works perfectly!

And there is another thing. Right now I am not Root, which means I can't openly edit all the files in the htdocs file as I would like to.

And I am gonna guess 'chmod 666' but isn't that insecure? Is there any problems with that?

Is there a way so only my account (Zaid) and Root can access the files only?

Thanks for taking the time to look at this,
_Logan_ ;)

---

### Post by Logan513 on 2010-05-07
Oh and btw;

I know that I could just use a simple html file for that but umm... well, my contact page is a bit more complicated and also doesn't work.

*cough*Code:

```
<head><title>Web Junkie - Web design service</title></head> 
<body background='img/bg.jpg' text='#FFFFFF' link='FFFF00' vlink='FFFF00' alink='FFFFFF'> 
<table width='60%' align='center'> 
       <tr> 
           <td> 
           <a href='index.php'><img src='img/logo.png' border='0'></a> 
           </td> 
       </tr> 
       <tr> 
           <td><br> 
               <table width='100%' bgcolor='#000000' border='1'> 
               <font face='courier new' color='white'> 
                     <tr align='center'> 
                         <td colspan='3'> 
                         <a href='index.php'>Home</a> | <a href='portfolio.php'>Portfolio</a> | <a href='pricing.php'>Pricing</a> | <a href='contact.php'>Contact us</a> 
                         </td> 
                     </tr> 
                     <tr> 
                         <td align='center'> 
                         <br>If you are interested in <i>Web Junkie's</i> services; E-mail us using the form below telling us what your website will be about*,<br>What package you are intersted in and whether or not you would like to host with us:<br><br> 
                         <font color='red'><b> 
 
                         <?php 
 
                         $date = date("D, M d - Y"); 
                         $time = date("h:i:s"); 
 
                         $to = "webjunkie@gmail.com"; 
                          
                         //when message sent message (message has been sent) make sure font color is set to green (#00FF00) 
 
                         if ($_POST['submit']){      //send check 
                           $name = $_POST['name']; 
                           $email = $_POST['email']; 
                           $subject = $_POST['subject']; 
                           $message = $_POST['message']; 
                           if ($name && $email && $subject && $message){ 
                              if (strlen($name)<=50 && strlen($email)<= 50 && strlen($subject) <= 50){  //length check 
 
                              } 
                              else 
                                  echo "50 characters max for the subject, name, and email! ;-)"; 
                           } 
                           else 
                               echo "Please enter something into <u>ALL</u> the fields. ;-)<br><br>"; 
                         } 
 
                         ?> 
 
                         </b></font> 
                         <form action='contact.php' method='POST'> 
                         <table align='center'> 
                                <tr> 
                                    <td> 
                                    Name: 
                                    </td> 
                                    <td> 
                                    <input type='text' maxlength='50' name='name'> 
                                    </td> 
                                </tr> 
                                <tr> 
                                     <td> 
                                     Email: 
                                     </td> 
                                     <td> 
                                     <input type='text' maxlength='50' name='email'> 
                                     </td> 
                                </tr> 
                                <tr> 
                                     <td> 
                                     Subject: 
                                     </td> 
                                     <td> 
                                     <input type='text' maxlength='50' name='subject'> 
                                     </td> 
                                </tr> 
                                <tr> 
                                     <td> 
                                     Message: 
                                     </td> 
                                </tr> 
                                <tr> 
                                    <td colspan='2'> 
                                    <textarea name='message' rows='10' cols='50'></textarea> 
                                    </td> 
                                </tr> 
                                <tr> 
                                    <td> 
                                    <input type='submit' name='submit' value='Send'> 
                                    </td> 
                                </tr> 
                         </table> 
                         </form><br> 
                         *We refuse to design and build porn and sexually explicit sites. 
                         <br><br> 
                         </td> 
                     </tr> 
                     <tr> 
                         <td colspan='3'> 
                         <div align='right'> 
                         Sight maintained by <i>Web Junkie</i> © 2010 
                         </div> 
                         </td> 
                     </tr> 
               </font> 
               </table> 
           </td> 
       </tr> 
</table> 
</body> 
</html>
```

---

### Post by Logan513 on 2010-05-07
Lemme go in as root and see if its a permission problem.

:-k

---

### Post by Logan513 on 2010-05-07
Nope same crap. :icon_frown:

---

### Post by Logan513 on 2010-05-07
Bump

---

### Post by Logan513 on 2010-05-07
C'mon guys! :mad:

---

### Post by Fefo_wa on 2013-05-04
cd opt/lampp/htdocs
sudo chmod -R 0777 "directory you want to change the permition"

it worked for me :D

---

### Post by oldos2er on 2013-05-04
Closed, please don't bump old threads.

---

