---
title: "Jquery Code not running..."
date: 2011-12-21
forum: General Help
---

### Post by deva99 on 2011-12-21
I am trying to run a simple jquery code on my linux ubuntu 11.04 pc. i am not able to execute the code. jquery is not running. please help me to find out whats the error.

*****************1.html****************************

<html>
    <head> <title> MY 1st page </title> </head>
    <body>
        <p id="start"> This is the testing page for Jquery!! </p>
        <script type="text/javascript" src="///home/devarshi/Jquery/extrn.js"></script>
        <script type="text/javascript" src="///home/devarshi/Jquery/jquery.js"></script>
            
    </body>
</html>

*************************************************

******************extrn.js**********************
$(document).ready(function(){
   alert('Document is ready !!');
   $('#start').fadeIn('slow');
});
************************************************

and the jquery.js is normal jquery file copied from jquery.org website....


Do i need to install any Apache or any server to run this code?? 

i was easily able to excute the jquery code in windows ...why i am not able to do it here?? 

HELP please!!!

---

