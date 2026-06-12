---
title: "Omega sign showing up as W"
date: 2010-01-08
forum: General Help
---

### Post by bobbywall87 on 2010-01-08
I am a student taking an online course in electronics, on my class web site the Omega sign is showing up as a W instead. I have tried to change the font even tried to import new fonts that might have the sign. I have also tried to change the character encoding nothing has worked and ideas I will try anything. I am running firefox 3.5 and ubuntu 9.10

---

### Post by Another Monkey on 2010-01-08
That's probably not a W, that's probably lower-case **o**mega (&#969;) as opposed to an upper-case **O**mega (&#937;).

The XHTML entity references are:
lowercase Omega, &#969;, &omega;
Uppercase Omega, &#937;, &Omega;
(Note the difference in casing after the "&").

---

### Post by bobbywall87 on 2010-01-08
here is a screen shot of the page as you can see it is clearly a W

---

### Post by Another Monkey on 2010-01-08
Ah right, it's not a page you have written yourself.

OK, that is weird.  Have you viewed to source of the page to see what's there?  (Right Click/View Page Source)

Might help if you can post that fragment (just that line) and maybe the encoding at the top of the page.

This is a very simple page the works for me when I tested it with UTF-8 encoding. It displays the omega character in two ways; as the actual character and using the entity symbol from above.  When you save this from gedit (e.g. as "test.html" to Desktop), make sure the encoding is UTF-8 and if you change that encoding, update the "meta" tag to match.
```
<html>
	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
	</head>
	<body>
		Lowercase omega:&nbsp;&#969;<br>
		Lowercase omega:&nbsp;&#937;<br>
		Uppercase omega:&nbsp;&omega;<br>
		Uppercase omega:&nbsp;&Omega;
	</body>
</html>
```

---

### Post by bobbywall87 on 2010-01-08
The code you posted worked i could see the Omega sing but the web page still doesn't i cant find the line in the source code i can post all of it if that would help


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">
<head id="ctl00_ctl00_Head1"><title>
	ASSESSMENT: Scientific and Engineering Notation
</title>
    <script language="javascript" type="text/javascript">
    var Page = function() { };
    </script>
    
    

<base href="[http://gvtc.angellearning.com/AngelUploads/Content/827_EET101_201003_K_30225/_assoc/e85db6b038234b22a0be2a1975b3520a/]("http://ubuntuforums.org/view-source:http://gvtc.angellearning.com/AngelUploads/Content/827_EET101_201003_K_30225/_assoc/e85db6b038234b22a0be2a1975b3520a/")"></base>
<link rel="stylesheet" type="text/css" href="[/AngelUploads/Files/e8176444-64aa-463a-a0fc-a7bb67932ef1/Stylesheets/Borpslub.css]("http://ubuntuforums.org/view-source:http://gvtc.angellearning.com/AngelUploads/Files/e8176444-64aa-463a-a0fc-a7bb67932ef1/Stylesheets/Borpslub.css")" /><link rel="stylesheet" type="text/css" href="[/AngelUploads/Files/e8176444-64aa-463a-a0fc-a7bb67932ef1/Stylesheets/Borpslub.css]("http://ubuntuforums.org/view-source:http://gvtc.angellearning.com/AngelUploads/Files/e8176444-64aa-463a-a0fc-a7bb67932ef1/Stylesheets/Borpslub.css")" /><SCRIPT LANGUAGE="JavaScript">if(!run){ document.write('<SCRI' + 'PT LANGUAGE="JavaScript" src="/jscript/Localization.js"><\/SCRIPT>'); var run = true; }</SCRIPT><script type="text/javascript" language="javascript" src="[/InlineEditor/fckeditor.js]("http://ubuntuforums.org/view-source:http://gvtc.angellearning.com/InlineEditor/fckeditor.js")"></script><script type="text/javascript" language="javascript" src="[/InlineEditor/inline.asp]("http://ubuntuforums.org/view-source:http://gvtc.angellearning.com/InlineEditor/inline.asp")"></script>

<script language="javascript" type="text/javascript">
<!--//
var gblnRefreshIndex = false;
var gstrAPI = '/api/default.asp';
var gstrAngelApp = 'CRSCNT';
var gstrWCI = '';
var gstrWCE = '';
var gstrFinalWCI = '';
var gstrFinalWCE = '';
var gstrScriptURL = 'http://gvtc.angellearning.com/section/content/Default.asp?WCU=CRSCNT';
var gstrPostURL = '';
var gstrBaseHref = 'http://gvtc.angellearning.com/AngelUploads/Content/827_EET101_201003_K_30225/_assoc/e85db6b038234b22a0be2a1975b3520a';
var gstrStylesheet = '/AngelThemes/Stylesheets/GVTC.css';
var glngUserRights = 2;
var gstrUserID = 'eb357cd4-34cf-487e-834c-18d32f87a982';
var gstrSectionID = '827_EET101_201003_K_30225';
var gstrRootID = 'ROOT';
var gstrParentID = '3a04ae0105de491c9fe257759450e978';
var gstrObjectID = '0b5cce8711a64bbc916f5c4774e7db41';
var gstrObjectType = 'ASSESSMENT';
var gstrBaseType = 'ASSESSMENT';
var gstrEntryID = 'e85db6b038234b22a0be2a1975b3520a';
var gstrEntrySection = '827_EET101_201003_K_30225';
var gstrEntryTitle = 'Scientific and Engineering Notation';
var gstrBoardID = '';
var gstrBoardTitle = '';
var gstrShortcutID = '';
var gstrShortcuts = '';
var gblnSubmit = true;
var gblnForceSubmitting = false;

//The same variables, but in a hierarchical structure
var LO = (function(){
    var constructor = function(){
    }
    
    return constructor;
})();

LO.API = gstrAPI;
LO.angelApp = gstrAngelApp;
LO.scriptURL = gstrScriptURL;
LO.postURL = '';
LO.baseHref = gstrBaseHref;
LO.stylesheet = gstrStylesheet;
LO.userRights = glngUserRights;
LO.userID = gstrUserID;
LO.sectionID = gstrSectionID;
LO.rootID = gstrRootID;
LO.parentID = gstrParentID;
LO.objectID = gstrObjectID;
LO.objectType = gstrObjectType;
LO.baseType = gstrBaseType;
LO.entryID = gstrEntryID;
LO.entrySection = gstrEntrySection;
LO.entryTitle = gstrEntryTitle;

var LearningObject = LO;

//-->
</script></head>
<body id="e85db6b038234b22a0be2a1975b3520a" class="bodyLessons cmTypeASSESSMENT PGDISPLAY_ASSESSMENT PGDISPLAY_ASSESSMENT_RESPOND">
    
    



    <form name="aspnetForm" method="post" action="Default.aspx?entryID=e85db6b038234b22a0be2a1975b3520a&amp;parentID=3a04ae0105de491c9fe257759450e978&amp;caller=%2fsection%2fcontent%2fDefault.asp&amp;WCI=pgDisplay_Object&amp;WCU=CRSCNT&amp;Preview=0" id="aspnetForm">
<div>
<input type="hidden" name="__EVENTTARGET" id="__EVENTTARGET" value="" />
<input type="hidden" name="__EVENTARGUMENT" id="__EVENTARGUMENT" value="" />
<input type="hidden" name="__VIEWSTATE" id="__VIEWSTATE" value="/wEPDwULLTE4MzU1NTk4NDYPZBYCZg9kFgJmD2QWAgIKD2QWAgIDDw8WAh4HVmlzaWJsZWhkZGQSXNNmnQ4lXNOdK9RMRKK7PPupTA==" />
</div>

<script type="text/javascript">
//<![CDATA[
var theForm = document.forms['aspnetForm'];
if (!theForm) {
    theForm = document.aspnetForm;
}
function __doPostBack(eventTarget, eventArgument) {
    if (!theForm.onsubmit || (theForm.onsubmit() != false)) {
        theForm.__EVENTTARGET.value = eventTarget;
        theForm.__EVENTARGUMENT.value = eventArgument;
        theForm.submit();
    }
}
//]]>
</script>


<script src="[/WebResource.axd?d=ptT7Zsa2xEZADaSLIXwmuA2&amp;t=633737208427582046]("http://ubuntuforums.org/view-source:http://gvtc.angellearning.com/WebResource.axd?d=ptT7Zsa2xEZADaSLIXwmuA2&t=633737208427582046")" type="text/javascript"></script>


<script src="[/JScript/HelpPopup.js]("http://ubuntuforums.org/view-source:http://gvtc.angellearning.com/JScript/HelpPopup.js")" type="text/javascript"></script>
<script src="[/jscript/jsActions.js]("http://ubuntuforums.org/view-source:http://gvtc.angellearning.com/jscript/jsActions.js")" type="text/javascript"></script>
<div>

	<input type="hidden" name="__PREVIOUSPAGE" id="__PREVIOUSPAGE" value="eXinqdVuWpzc000OEdZxoTqe9ofiogAroYtKbZEDqjnUOXRnjM6mWIZyP4NLtNxG0" />
</div>
        <div class="normalDiv">
            <div class="normalSpan">
                <div id=&#8221;subject_image&#8221;></div>
                
    
    
	<big><strong><span class="titleSpan">
		<span id="ctl00_ctl00_contentArea_belowToolbar_instructionsTitle">Instructions</span>
	</span></strong></big><br /><br />
    <div class="normalDiv">
        <span class="normalSpan">
			<table id="ctl00_ctl00_contentArea_belowToolbar_assessmentInfo" border="0">
	<tr valign="top">
		<td id="ctl00_ctl00_contentArea_belowToolbar_instructionsText" style="width:50%;"><span id="ctl00_ctl00_contentArea_belowToolbar_instructorGeneratedText"><div>
<p>Look at this symbol:&nbsp; <span style="font-size: 12pt"><span style="font-size: 12pt"><span style="font-family: Symbol; font-size: 12pt">W</span></span></span><br />
If you see an omega, or ohms symbol, then you're ok.&nbsp; But if you see a W, you browser is not correctly displaying characters and you need to fix this setting before doing this homework assignment.</p>
</div></span><br /><ul id="ctl00_ctl00_contentArea_belowToolbar_settingsList" style="margin-left:1px; padding-left:1em;">
			<li>This assessment is not tied to a gradebook assignment</li><li>Maximum number of attempts: Unlimited</li><li>Time limit: Unlimited minutes</li><li>Review mode: Full</li>
		</ul>
			            <br /><br /><input type="submit" name="ctl00$ctl00$contentArea$belowToolbar$beginButton" value="Resume" onclick="javascript:WebForm_DoPostBackWithOptions(new WebForm_PostBackOptions(&quot;ctl00$ctl00$contentArea$belowToolbar$beginButton&quot;, &quot;&quot;, false, &quot;&quot;, &quot;[http://gvtc.angellearning.com/Section/Assessment/Delivery/AssessmentLanding.aspx?entryId=e85db6b038234b22a0be2a1975b3520a&quot;](http://gvtc.angellearning.com/Section/Assessment/Delivery/AssessmentLanding.aspx?entryId=e85db6b038234b22a0be2a1975b3520a&quot;), false, false))" id="ctl00_ctl00_contentArea_belowToolbar_beginButton" /><br />
			            <span id="ctl00_ctl00_contentArea_belowToolbar_beginStatusLabel">Unlimited attempts available</span></td><td id="ctl00_ctl00_contentArea_belowToolbar_submissionTable" style="width:30%;"><div id="ctl00_ctl00_contentArea_belowToolbar_AssessmentReview1_emptyView">
			
		<table summary="" border="1" cellpadding="2" cellspacing="0"  style="text-align:center">
			<tr>
				<td align="left">
					<span style="font-style:normal; font-size:medium;">
						<p>No submissions have been recorded for this assignment.</p>
						<p>Submissions for this assignment will appear in this area.</p>
					</span>
				</td>
			</tr>
		</table>

		</div>


</td>
	</tr>
</table><br />
            </span>
        </div>
        
            <div>
                <p>
                    
                </p>
            </div>
        
        
        <!-- Agents & Actions -->
        <div id="ActionMessages"></div>


    <div style="margin-top:.7em;width:100%">
        
    </div>

            </div>
        </div>
    

<script type="text/javascript">
//<![CDATA[
issueRedirect((parent && parent.location && parent.frames && parent.frames.length > 0 && parent.frames[0].name == 'lsn_header') ? parent : null);//]]>
</script>
</form>
    
    <div class="normalDiv">
    <div class="normalSpan">    
        
    

    
    
    <script  type="text/javascript" language="Javascript">
        setTimeout(function()
                    {
                        if (parent.parent.ANGEL && parent.parent.ANGEL.ui && parent.parent.ANGEL.ui.bc) 
                        { 
                            if(this.parent.name == "AngelContent")
                            {
                                parent.parent.ANGEL.ui.bc.update(this.parent); 
                            }
                            else if(this.name == "AngelContent")
                            {
                                parent.parent.ANGEL.ui.bc.update(this); 
                            }
                        }
                        document.close();
                    }
            ,0);
    </script>
        
                
    </div>
    </div>    
</body>
</html>

---

### Post by MakotoTheKnight on 2010-01-08
Does this page render properly?

[http://en.wikipedia.org/wiki/Omega](http://en.wikipedia.org/wiki/Omega)

---

### Post by bobbywall87 on 2010-01-08
As far as i can tell i posted a screen shot of the page

---

### Post by Another Monkey on 2010-01-08
I see the problem
```
<span style="font-size: 12pt">
  <span style="font-size: 12pt">
    <span style="font-family: Symbol; font-size: 12pt">W</span>
  </span>
</span><br />
If you see an omega, or ohms symbol, then you're ok.&nbsp; But...
```
If you look in the middle span tag, you will see the character is actually a "W".  They expect it to display as Omega because they expect everyone to have a "Symbol" font.  Their explanation is also incorrect, your browser *is* showing the correct character; just not in the expected font.

Your solution should be simple - install a font with the name "Symbol" and try again.  I am afraid I am not on an Ubuntu system just now, but it should be pretty quick and easy to do.  (There's a thread about it [here]("http://ubuntuforums.org/showthread.php?t=210277").)

I guess they are doing it this way to try and cope with the <rude words removed> that is IE6.  Or they simply expect all their users to be running Windows.  Either way, it's not very good IMHO.  If I were you, I would let them know (may affect Mac users too I guess, and many people using netbooks).

---

### Post by junapp on 2010-01-08
> **Another Monkey said:**
>  Either way, it's not very good IMHO.
agreed. very poor given the html equivalents.

@bobbywall87: I have done what Another Monkey suggests. Copied the symbol.ttf from a windows font directory (for me was c:\windows\fonts) into ~/.fonts/

Then created a little html page with
[html]
<html>
<body>
<span style="font-family: Symbol; font-size: 12pt">W</span>
</body>
</html>
[/html]
which shows the little omega just fine after having the symbol font installed.

---

