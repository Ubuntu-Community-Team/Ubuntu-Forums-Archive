---
title: "AJAX- Always in ready state"
date: 2009-09-24
forum: General Help
---

### Post by Black Mage on 2009-09-24
The problem currently exist here, [http://www.prtrack.net/mypolls.php](http://www.prtrack.net/mypolls.php) but its not actually visible unless you are a member so it goes something like this:

I have a function in the javascript that updates a div. The function is this:

```

function updateComboBox(dataSource1, divID1,division, sport){
	  
	
	     XMLHttpRequestObject=getXmlHttpRequestObject();
	
	if( XMLHttpRequestObject){
		var obj = document.getElementById(divID1);
		
		XMLHttpRequestObject.open("POST", dataSource1);
		XMLHttpRequestObject.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
		
		XMLHttpRequestObject.onreadystatechange = function()
		{
			if (XMLHttpRequestObject.readyState == 4 && XMLHttpRequestObject.status == 200) {
				obj.innerHTML=XMLHttpRequestObject.responseText;
			}
			else if( XMLHttpRequestObject.readyState == 0){
				obj.innerHTML="..";
			}
			else if( XMLHttpRequestObject.readyState == 1){
				obj.innerHTML="Loading..";
			}
			else if( XMLHttpRequestObject.readyState == 2){
				obj.innerHTML="Loading....";
			}
			else if( XMLHttpRequestObject.readyState == 3){
				obj.innerHTML="Loading......";
			}
		}
		XMLHttpRequestObject.send("division=" + division + "&sport=" + sport);
	}
	 
	  
  }//end update


```

And it is called twice through a select box:

```

 <select name="division_box" id="division_box" class="combobox" id="division_box" onchange="updateComboBox('phpscripts/mypolls/refresh_conference.php',  'conference_Inner_Div',  this.form.division_box.value, this.form.sport_box.value);  updateComboBox('phpscripts/mypolls/refresh_region.php','regionInnerDiv', this.form.division_box.value, this.form.sport_box.value); ">
</select>

```

The problem is, only one div is changed while the other remains in readystate==1, always loading.

Does anyone know what can be causing this problem and how to solve it?


Thanks

---

