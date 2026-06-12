---
title: "Weird Javascript issue with Internet Explorer 7"
date: 2010-12-29
forum: General Help
---

### Post by Maheriano on 2010-12-29
Can we ask Windows questions here anymore?

I'm doing an online ordering system for a nationwide PPE supplier and I set it up so they can select the size and quantity they want of each item. Then if they want more sizes and quantities, they click a + button to add another row of select boxes to choose from. For some reason the select boxes are showing up above/below one another instead of beside each other and it's only happening in Internet Explorer 7. It works perfectly in Internet Explorer 8, Chrome and Firefox, however they don't use neither of those.

So I cut the code down immensely to just these few lines and completely removed the CSS so what you see is what I have and it still doesn't work. Anyone know why?

This is a div with 2 more divs inside of it which are supposed to line up next to one another, and each div has a select box inside. The idea is the first div will be the row and the inside divs will be columns. This code is hardcoded onto the page and displays perfectly in all browsers:
```

<div style="position:relative;width:500px;">
                       <div style="float:left;display:inline;">
                                     <select style="display:inline;"></select>
                       </div>
                       <div style="float:left;display:inline;">
                                      <select style="display:inline;"></select>
                        </div>
</div>

```

Then I constructed a Javascript function to spit out the same thing and when I use the Inspect Element function in Chrome it shows me the exact same code:
```
<div style="position:relative;width:500px;">
				<div style="float:left;display:inline;">
					<select style="display:inline;"></select>
				</div>
				<div style="float:left;display:inline;">
					<select style="display:inline;"></select>
				</div>
			</div>

```
The crazy problem is when I view the first one that is coded into the page, they appear side by side as they're supposed to. When I click the + button and run the Javascript to add the second code, the new select boxes appear above/below one another. Why is that? Why do they show the same code in Chrome and display differently in Internet Explorer?

Here is the Javascript function:

```
function addRow(id, nnn)
{
	if (!document.getElementsByTagName) return;
	formBody = document.getElementsByTagName("form").item(0);
	formElement = document.getElementById("formitem" + id);

	divRow = document.createElement("div");

select1 = document.createElement("select");
select2 = document.createElement("select");
select1.setAttribute("style", "display:inline;");
select2.setAttribute("style", "display:inline;");

ddd1 = document.createElement("div");
ddd2 = document.createElement("div");
ddd3 = document.createElement("div");
ddd1.setAttribute("style", "float:left;display:inline;");
ddd2.setAttribute("style", "float:left;display:inline;");
ddd3.setAttribute("style", "position:relative;width:500px;");

ddd1.appendChild(select1);
ddd2.appendChild(select2);
ddd3.appendChild(ddd1);
ddd3.appendChild(ddd2);


formBody.insertBefore(ddd3, formElement.nextSibling);

}
```

---

### Post by Maheriano on 2010-12-29
I might have figured this out, I tried using ddd1.style.display = 'inline'; instead of ddd1.setAttribute("style", "display:inline;"); and it works for my test code. I have to add the rest of the code back and see if it continues to work, is the setAttribute function not compatible with certain browsers or something?

---

