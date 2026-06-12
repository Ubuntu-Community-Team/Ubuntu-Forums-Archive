---
title: "Javascript and PHP Help!"
date: 2011-02-14
forum: General Help
---

### Post by Jovenrp on 2011-02-14
How can I pass a value of a javascript variable to a php variable within the same page?

var x = document.getElementById('propid').value;

document.getElementById("defenses").innerHTML = "<?php
    echo $sql_defname = "select def_name, def_id from defense where def_id IN (select def_type from schedules where prop_id =".VAR X." and status = 1)";

i need to put the value of var x to the mysql query inside the php.. the VAR X inside the mysql query should be the value of the javascript variable which is var x.

Thanks!

---

### Post by An Sanct on 2011-02-14
Well, PHP is server side, js is client side.

So the user (browser) will never see "<?php" in your page (unless the server is not working correctly!), but you can do it ...
[javascript -> PHP]("http://www.ajaxprojects.com/ajax/tutorialdetails.php?itemid=510")
[PHP -> javascript]("http://devzone.zend.com/article/1300")

And there are always "POST" options...

---

### Post by Jovenrp on 2011-02-14
Thanks! But thats not what Im looking for, Im looking for a way where I can get the value of the javascript in a function and pass it to a php variable but the php variable is also inside the javascript function.


function sample()
{
var x;
x = document.getElementById('id).value;

//now I need the "x" to be pass to a php variable which is also inside this function.

document.getElementByd('php').innerHTML = "<?php echo "variable is : ".$php." <---" ?>";

// Im going to put the var x inside the $php. How can I do it?
}

---

### Post by An Sanct on 2011-02-15
Yes, my way is clumsy, but it works ... somehow

The main problem is the "*side*" as PHP is server *side* and javascript client *side*, they have no way of interacting, unless you post values back and forth. For example IE under a default sound scheme gives away a set of annoying "clicks", when windows update is performed, asking the client what he has and bringing it back to the server.

Another way of "solving" (another not "so good" way) is to store a cookie, reload the page and post back the value.

---

