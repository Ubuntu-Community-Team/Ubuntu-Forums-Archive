---
title: "Website authentication"
date: 2010-06-08
forum: General Help
---

### Post by gameguy on 2010-06-08
I'm trying to create a website and don't know HTML very well (but I do know python and would also be interested if someone could help me run python code from HTML). I was wondering if anyone knew why, if I fill in the username as either first, second, or third, and the corresponding password, it doesn't go to main.html. It worked before I changed it to arrays instead of one user. And does anyone know which sites are good for learning HTML?

  <form>
#gets ursp + pwdp values
    <p align="center"><input onclick="javascript:validate(usrp.value, pwdp.value)" value="Log In" type="button" name="Submit"></p>
  </form><script language="javascript" type="text/javascript">

function validate(text1,text2){
 var user = new Array("first", "second", "third");
 var pwd = new Array("firstpwd", "secondpwd", "thirdpwd");
 var counter = 0;
 while (counter < length(user))
  {
  if (user[counter]==text1 && pwd[counter]==text2);
   {
   load('main.html');
   break
   }
  if (user[counter]!=text1 && counter == length(user))
   {
   load('failure.htm');
   }
  if (pwd[counter]!=text2 && counter == length(user))
   {
   load('failure.htm');
   }
  }
}
Thanks.

---

