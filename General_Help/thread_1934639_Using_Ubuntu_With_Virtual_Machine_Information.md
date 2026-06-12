---
title: "Using Ubuntu With Virtual Machine Information"
date: 2012-03-02
forum: General Help
---

### Post by GodveX on 2012-03-02
Hello,

I am a fan of linux operating systems but i have run into a small problem. The problem i am facing is i am currently undergoing a diploma in programming and last semester was java based so the OS was not a problem for me. This semester i have to use ASP.NET & MS SQL. 

If i keep my linux operating system and install a virtual machine with windows to only run visual studio and MS SQL will i run into problems? 

What i will be doing is a small software project something similar to game & play website (e-commerce) so i will be connecting MS SQL & ASP.NET to make this happen.

Any type of information is welcome

thanks in advance
GodveX

---

### Post by josephmills on 2012-03-02
> **GodveX said:**
> Hello,

I am a fan of linux operating systems but i have run into a small problem. The problem i am facing is i am currently undergoing a diploma in programming and last semester was java based so the OS was not a problem for me. This semester i have to use ASP.NET & MS SQL. 

If i keep my linux operating system and install a virtual machine with windows to only run visual studio and MS SQL will i run into problems? 

What i will be doing is a small software project something similar to game & play website (e-commerce) so i will be connecting MS SQL & ASP.NET to make this happen.

Any type of information is welcome

thanks in advance
GodveX


I like to use [MONO](http://monodevelop.com/) it is in the repos. If you like I am live streaming here I could show a little rundown of mono with asp or VB [http://www.justin.tv/tuxforprez#/w/2697823440](http://www.justin.tv/tuxforprez#/w/2697823440)

---

### Post by GodveX on 2012-03-02
sure mate would love to see how mono works never tried if before although i have heard of it watching the live streaming now

Edit: still watching your live stream does mono support drag & drop tools for textboxes, buttons etc. and does it show the design tab ?

ps: thanks for your time mate

---

### Post by drdos2006 on 2012-03-02
As long as you have allocated enough hard drive space to your Virtual Harddrive, there is no reason that you cannot run the Windows OS, the MS SQL server and Visual Studio from your virtual  machine. If your RAM is at least 2 Gigs then you should be OK.

regards

---

### Post by jerome1232 on 2012-03-02
> **drdos2006 said:**
> As long as you have allocated enough hard drive space to your Virtual Harddrive, there is no reason that you cannot run the Windows OS, the MS SQL server and Visual Studio from your virtual  machine. If your RAM is at least 2 Gigs then you should be OK.

regards

+1 A virtual machine is probably the way to go since this is for school, a virtual machine is for all intents and purposes like a real windows installation, your not likely to run into any problems. You will need a valid windows license (shouldn't be too expensive as you are a student)

I personally like Oracles VirtualBox

---

### Post by GodveX on 2012-03-02
i will be trying out the virtual machine method tomorrow my ram is 4gb so i should not run into any problems as for licenses they are also covered visual studio 2010, win7 etc thanks for your replies

---

### Post by imachavel on 2012-03-02
yes I like oracles virtual box. Great people those Oracle, hmmm... I wonder, do they have anything to do with linux kernel development and gui development? REDHAD Maybe?? Haha..

I don't know if sql will work in Linux. Never tried it. As you said apache and compiled java(java.class once compiled right?) work great. Now asp.net, well figure out local host, asp.net is not TOO different from html. I'm not sure the different features. I believe you can save an html file as index.html or index.aspx and .net I'm not sure if it works as a back end or if it's also front end. Just learn tags

<body>

<header>

<p>

</p>

actually here is a more well explained solution:

Examples
[edit]Inline code
<%@ Page Language="C#" %>
<!DOCTYPE html PUBLIC "---//W3C//DTD XHTML 1.0  //EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<script runat="server">
  protected void Page_Load(object sender, EventArgs e)
  {
    // Assign the datetime to label control
    lbl1.Text = DateTime.Now.ToLongTimeString();
 
  }
</script>
 
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
  <title>Sample page</title>
</head>
<body>
  <form id="form1" runat="server">
 
    <div>
      The current time is: <asp:Label runat="server" id="lbl1" />
    </div>
  </form>
</body>
</html>
The above page renders with the Text "The current time is: " and the <asp:Label> Text is set with the current time, upon render.
[edit]Code-behind solutions
<%@ Page Language="C#" CodeFile="SampleCodeBehind.aspx.cs" Inherits="Website.SampleCodeBehind"
AutoEventWireup="true" %>
The above tag is placed at the beginning of the ASPX file. The CodeFile property of the @ Page directive specifies the file (.cs or .vb or .fs) acting as the code-behind while the Inherits property specifies the Class from which the Page is derived. In this example, the @ Page directive is included in SampleCodeBehind.aspx, then SampleCodeBehind.aspx.cs acts as the code-behind for this page:
using System;
namespace Website
{
  public partial class SampleCodeBehind : System.Web.UI.Page
  {
    protected void Page_Load(object sender, EventArgs e)
    {
      Response.Write("Hello, world");
    }
  }
}
Imports System
Namespace Website
  Public Partial Class SampleCodeBehind 
          Inherits System.Web.UI.Page
          Protected Sub Page_Load(ByVal sender As Object, ByVal e As EventArgs)
             Response.Write("Hello, world")
          End Sub
  End Class
End Namespace
In this case, the Page_Load() method is called every time the ASPX page is requested. The programmer can implement event handlers at several stages of the page execution process to perform processing.


very complex hello world but why not. now with windows and linux, obviously the code might not look exactly the same. the method might be different. But man will it be similar, it'll be so similar, and the concept will be so extremely similar. With c code I'm not sure if c is compiled in windows the same as linux, which would be

gcc -o (file input) (file destination)

I believe then opened

./(filename.c)

I'm no programming expert but man am I trying

---

### Post by imachavel on 2012-03-02
> **GodveX said:**
> i will be trying out the virtual machine method tomorrow my ram is 4gb so i should not run into any problems as for licenses they are also covered visual studio 2010, win7 etc thanks for your replies

ram with 4gb is no big deal, but vm share all memory, ESPECIALLY processor. You can set the settings for what each i/o device uses in terms of what the host gets and what the vm gets. But for processor you can't change anything as it's being shared on the host, if either the guest OS running as a program or the host OS bottlenecks both OSes will bottleneck extensively. If you have a mobo with more then one processor, it'll help you can set number of cached processors in the settings. So host will use whatever is set in the bios, and guest can't use more then that. But at the same time guest can use only one processor if you don't want the host to slow down. If you want maximum processing and caching and paging ability for guest, use maximum number or processors. If you can't afford a build made with a $500 dual or $700 quad socket board, and the price of four processors each totaling probably $200 - $400, I don't blame you of course. The price of all that plus a printer, phone, network, other bills, is quite a total :popcorn:

---

### Post by GodveX on 2012-03-02
> **imachavel said:**
> yes I like oracles virtual box. Great people those Oracle, hmmm... I wonder, do they have anything to do with linux kernel development and gui development? REDHAD Maybe?? Haha..

I don't know if sql will work in Linux. Never tried it. As you said apache and compiled java(java.class once compiled right?) work great. Now asp.net, well figure out local host, asp.net is not TOO different from html. I'm not sure the different features. I believe you can save an html file as index.html or index.aspx and .net I'm not sure if it works as a back end or if it's also front end. Just learn tags

<body>

<header>

<p>

</p>

actually here is a more well explained solution:

Examples
[edit]Inline code
<%@ Page Language="C#" %>
<!DOCTYPE html PUBLIC "---//W3C//DTD XHTML 1.0  //EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<script runat="server">
  protected void Page_Load(object sender, EventArgs e)
  {
    // Assign the datetime to label control
    lbl1.Text = DateTime.Now.ToLongTimeString();
 
  }
</script>
 
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
  <title>Sample page</title>
</head>
<body>
  <form id="form1" runat="server">
 
    <div>
      The current time is: <asp:Label runat="server" id="lbl1" />
    </div>
  </form>
</body>
</html>
The above page renders with the Text "The current time is: " and the <asp:Label> Text is set with the current time, upon render.
[edit]Code-behind solutions
<%@ Page Language="C#" CodeFile="SampleCodeBehind.aspx.cs" Inherits="Website.SampleCodeBehind"
AutoEventWireup="true" %>
The above tag is placed at the beginning of the ASPX file. The CodeFile property of the @ Page directive specifies the file (.cs or .vb or .fs) acting as the code-behind while the Inherits property specifies the Class from which the Page is derived. In this example, the @ Page directive is included in SampleCodeBehind.aspx, then SampleCodeBehind.aspx.cs acts as the code-behind for this page:
using System;
namespace Website
{
  public partial class SampleCodeBehind : System.Web.UI.Page
  {
    protected void Page_Load(object sender, EventArgs e)
    {
      Response.Write("Hello, world");
    }
  }
}
Imports System
Namespace Website
  Public Partial Class SampleCodeBehind 
          Inherits System.Web.UI.Page
          Protected Sub Page_Load(ByVal sender As Object, ByVal e As EventArgs)
             Response.Write("Hello, world")
          End Sub
  End Class
End Namespace
In this case, the Page_Load() method is called every time the ASPX page is requested. The programmer can implement event handlers at several stages of the page execution process to perform processing.


very complex hello world but why not. now with windows and linux, obviously the code might not look exactly the same. the method might be different. But man will it be similar, it'll be so similar, and the concept will be so extremely similar. With c code I'm not sure if c is compiled in windows the same as linux, which would be

gcc -o (file input) (file destination)

I believe then opened

./(filename.c)

I'm no programming expert but man am I trying

easy coding there mate :P true it is not much different from html except you can code behind the .aspx pages for the website. To be honest i prefer Java as a programming language and also php i am not a big microsoft fan :/ the only reason i am going to install vs is because of school

---

