---
title: "Help me learn struts"
date: 2011-01-03
forum: General Help
---

### Post by Maheriano on 2011-01-03
I know most programming languages and run a web development business but haven't dealt much with struts yet. I've spent this evening reading up on them and I have a few questions as to why someone might use them.

1. I see they are sort of like an API extension to the Java EE platform allowing you to create more scalable applications. Since Java's main selling point is that it's cross platform, why would it be useful in a web environment where the platform is irrelevant? Why not use PHP instead? Or .NET?

2. It seems to be most helpful when developing a MVC type architecture which makes sense but isn't it easy enough to create this tiered architecture with the API we already have available? Why do we need these struts?

3. I see these were used to create Drupal, Joomla! and Ruby, why couldn't those applications simply be created with PHP?

---

### Post by wild_oscar on 2011-01-04
> **Maheriano said:**
> 
1. I see they are sort of like an API extension to the Java EE platform allowing you to create more scalable applications. Since Java's main selling point is that it's cross platform, why would it be useful in a web environment where the platform is irrelevant? Why not use PHP instead? Or .NET?


Struts is an MVC framework, not an API extension.
As to platform being irrelevant, not quite. You're forgetting about the servers the web application runs in. If you develop it in .Net, try serving the application on a Linux machine...

> 
2. It seems to be most helpful when developing a MVC type architecture which makes sense but isn't it easy enough to create this tiered architecture with the API we already have available? Why do we need these struts?


How would you serve the web pages with the Java API? Where would you store the html? I guess you should read a bit of web server's history, Java servlets and how Struts came to existence. And, of course, answer to the question: why do you want to learn it?

---

### Post by Maheriano on 2011-01-05
Okay I got a few more questions about this now.
```
// structure/calc-mvc/CalcMVC.java -- Calculator in MVC pattern.
// Fred Swartz -- December 2004

import javax.swing.*;

public class CalcMVC {
    //... Create model, view, and controller.  They are
    //    created once here and passed to the parts that
    //    need them so there is only one copy of each.
    public static void main(String[] args) {
        
        CalcModel      model      = new CalcModel();
        CalcView       view       = new CalcView(model);
        CalcController controller = new CalcController(model, view);
        
        view.setVisible(true);
    }
}
```
So this completely makes sense, just initialize the constructors for each class and then load the view. Will the main class pretty much look like this for every MVC application?

```
// structure/calc-mvc/CalcView.java - View component
//    Presentation only.  No user actions.
// Fred Swartz -- December 2004

import java.awt.*;
import javax.swing.*;
import java.awt.event.*;

class CalcView extends JFrame {
    //... Constants
    private static final String INITIAL_VALUE = "1";
    
    //... Components
    private JTextField m_userInputTf = new JTextField(5);
    private JTextField m_totalTf     = new JTextField(20);
    private JButton    m_multiplyBtn = new JButton("Multiply");
    private JButton    m_clearBtn    = new JButton("Clear");
    
    private CalcModel m_model;
    
    //======================================================= constructor
    /** Constructor */
    CalcView(CalcModel model) {
        //... Set up the logic
        m_model = model;
        m_model.setValue(INITIAL_VALUE);
        
        //... Initialize components
        m_totalTf.setText(m_model.getValue());
        m_totalTf.setEditable(false);
        
        //... Layout the components.      
        JPanel content = new JPanel();
        content.setLayout(new FlowLayout());
        content.add(new JLabel("Input"));
        content.add(m_userInputTf);
        content.add(m_multiplyBtn);
        content.add(new JLabel("Total"));
        content.add(m_totalTf);
        content.add(m_clearBtn);
        
        //... finalize layout
        this.setContentPane(content);
        this.pack();
        
        this.setTitle("Simple Calc - MVC");
        // The window closing event should probably be passed to the 
        // Controller in a real program, but this is a short example.
        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
    
    void reset() {
        m_totalTf.setText(INITIAL_VALUE);
    }
    
    String getUserInput() {
        return m_userInputTf.getText();
    }
    
    void setTotal(String newTotal) {
        m_totalTf.setText(newTotal);
    }
    
    void showError(String errMessage) {
        JOptionPane.showMessageDialog(this, errMessage);
    }
    
    void addMultiplyListener(ActionListener mal) {
        m_multiplyBtn.addActionListener(mal);
    }
    
    void addClearListener(ActionListener cal) {
        m_clearBtn.addActionListener(cal);
    }
}
```
So this simply loads the view that is seen by the end user and doesn't contain any of the logic used by the application. But I'm wondering why the view is calling the setText methods, shouldn't these be done by the controller? What's the controller's job if not to facilitate the communication between the view and the model?

```
// structure/calc-mvc/CalcModel.java
// Fred Swartz - December 2004
// Model
//     This model is completely independent of the user interface.
//     It could as easily be used by a command line or web interface.

import java.math.BigInteger;

public class CalcModel {
    //... Constants
    private static final String INITIAL_VALUE = "0";
    
    //... Member variable defining state of calculator.
    private BigInteger m_total;  // The total current value state.
    
    //============================================================== constructor
    /** Constructor */
    CalcModel() {
        reset();
    }
    
    //==================================================================== reset
    /** Reset to initial value. */
    public void reset() {
        m_total = new BigInteger(INITIAL_VALUE);
    }
    
    //=============================================================== multiplyBy
    /** Multiply current total by a number.
    *@param operand Number (as string) to multiply total by.
    */
    public void multiplyBy(String operand) {
        m_total = m_total.multiply(new BigInteger(operand));
    }
    
    //================================================================= setValue
    /** Set the total value. 
    *@param value New value that should be used for the calculator total. 
    */
    public void setValue(String value) {
        m_total = new BigInteger(value);
    }
    
    //================================================================= getValue
    /** Return current calculator total. */
    public String getValue() {
        return m_total.toString();
    }
}
```
This also makes sense, it's the basic functions of get, set and multiply used by the application.

```
// stucture/calc-mvc/CalcController.java - Controller
//    Handles user interaction with listeners.
//    Calls View and Model as needed.
// Fred Swartz -- December 2004

import java.awt.event.*;

public class CalcController {
    //... The Controller needs to interact with both the Model and View.
    private CalcModel m_model;
    private CalcView  m_view;
    
    //========================================================== constructor
    /** Constructor */
    CalcController(CalcModel model, CalcView view) {
        m_model = model;
        m_view  = view;
        
        //... Add listeners to the view.
        view.addMultiplyListener(new MultiplyListener());
        view.addClearListener(new ClearListener());
    }
    
    
    ////////////////////////////////////////// inner class MultiplyListener
    /** When a mulitplication is requested.
     *  1. Get the user input number from the View.
     *  2. Call the model to mulitply by this number.
     *  3. Get the result from the Model.
     *  4. Tell the View to display the result.
     * If there was an error, tell the View to display it.
     */
    class MultiplyListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            String userInput = "";
            try {
                userInput = m_view.getUserInput();
                m_model.multiplyBy(userInput);
                m_view.setTotal(m_model.getValue());
                
            } catch (NumberFormatException nfex) {
                m_view.showError("Bad input: '" + userInput + "'");
            }
        }
    }//end inner class MultiplyListener
    
    
    //////////////////////////////////////////// inner class ClearListener
    /**  1. Reset model.
     *   2. Reset View.
     */    
    class ClearListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            m_model.reset();
            m_view.reset();
        }
    }// end inner class ClearListener
}
```
This is the controller that listens to the buttons and performs actions when the user interacts with the application. Is this the sole purpose of the controller or is it supposed to do the calls for get/set as well? I pretty much got it now, just have these last few questions, thanks.

---

