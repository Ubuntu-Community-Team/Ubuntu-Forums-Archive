---
title: "Is there something I have to enable/configure to get this to work?"
date: 2011-12-21
forum: General Help
---

### Post by bignixs on 2011-12-21
Hi I have a module enabled on my site and it does not work on my ubuntu home server, it completes all the steps except for the last step, it just goes blank. I have tried this module on my web hosting provider and it works great, but when I try it on my ubuntu home server then it does not complete the last step... why? Is there something I have to enable in ubuntu?

Here is a link to my site that is on my ubuntu home server:

[https://www.5-on-it.com/](https://www.5-on-it.com/)

When you add a product to your cart and checkout using the authorize.net payment method, you can checkout using all the steps except for the last step. It does not complete on my personal ubuntu but it works perfectly fine on my paid hosting. So I would think that something is not enabled or installed.

I have my website files in this directory:  /var/www/

Either something is not enabled/installed on my server or my server is not picking up all the links/includes in the code... I am not sure and don't know.

Here is the code of each file of the module:

confirm-payment.tpl:

```
{capture name=path}{l s='Credit Card Payment'}{/capture}
{include file=$tpl_dir./breadcrumb.tpl}

<h2>{l s='Confirm Order' mod='payauthorizenet'}</h2>

{assign var='current_step' value='payment'}


{include file=$tpl_dir./errors.tpl}

{*<h3>{l s='Credit Card Payment' mod='payauthorizenet'}</h3>*}

{literal}

    <script type="text/javascript">
    $(document).ready(function(){
        
        //Hide div w/id extra
       $("#cart").css("display","none");

        // Add onclick handler to checkbox w/id checkme
       $("#cartselect").click(function(){
        
        // If checked
        if ($("#cartselect").is(":checked"))
        {
            
            $("#cart").show("fast");
        }
        else
        {       
    
            $("#cart").hide("fast");
        }
      });
    
        });
     </script>
{/literal}

{if isset($empty)}
    <p class="warning">{l s='Your Shopping Cart Is Empty'}</p>
{else}
<form method="post">
<b><p class="align_center"><input type="checkbox" id="cartselect" name="cartselect" value="1" {if $cart->cartselect == 1}checked="checked"{/if}> - <img src="img/ionexpress/cart.gif" alt="View Cart" align="absmiddle"/> &nbsp;{l s='View Shopping Cart'}<br /><br /></b></p>
</form>

<div id="cart">
<div id="order-detail-content" class="table_block">
    <table id="cart_summary" class="std">
        <thead>
            <tr>
                <th class="cart_product first_item">{l s='Product'}</th>
                <th class="cart_description item">{l s='Description'}</th>
                <th class="cart_ref item">{l s='SKU'}</th>
                <th class="cart_availability item">{l s='Avail.'}</th>
                <th class="cart_unit item">{l s='Price'}</th>
                <th class="cart_quantity item">{l s='Qty'}</th>
                <th class="cart_total last_item">{l s='Total'}</th>
            </tr>
        </thead>
        <tfoot>
            <tr class="cart_total_product">
                <td colspan="6">{l s='Total Products:'}</td>
                <td class="price">{convertPrice price=$total_products}</td>
            </tr>
            <tr class="cart_total_product">
                <td colspan="6">{l s='Tax:'}</td>
                <td class="price">{convertPrice price=$total_tax}</td>
            </tr>
            {if $total_discounts > 0}
            <tr class="cart_total_voucher">
                <td colspan="6">{l s='Total Coupons:'}</td>
                <td class="price-discount">{convertPrice price=$total_discounts}</td>
            </tr>
            {/if}
            {if $total_wrapping > 0}
            <tr class="cart_total_voucher">
                <td colspan="6">{l s='Total Gift-Wrapping:'}</td>
                <td class="price-discount">{convertPrice price=$total_wrapping}</td>
            </tr>
            {/if}
            {if $shippingCost > 0}
            <tr class="cart_total_delivery">
                <td colspan="6">{l s='Total Shipping:'}</td>
                <td class="price">{convertPrice price=$shippingCost}</td>
            </tr>
            {/if}
            <tr class="cart_total_price">
                <td colspan="6" style="border-bottom: 1px solid #bdc2c9;">{if !$carrier->id}{l s='Total:'}{else}{l s='Total:'}{/if}</td>
                <td class="price" style="border-bottom: 1px solid #bdc2c9;">{convertPrice price=$total_price}</td>
            </tr>
        </tfoot>
        <tbody>
        {foreach from=$products item=product name=productLoop}
            <tr class="{if $smarty.foreach.productLoop.last}last_item{elseif $smarty.foreach.productLoop.first}first_item{/if} {if $smarty.foreach.productLoop.index % 2}alternate_item{else}item{/if} cart_item">
                <td class="cart_product">
                    <a href="{$link->getProductLink($product.id_product, $product.link_rewrite)|escape:'htmlall':'UTF-8'}"><img src="{$img_prod_dir}{$product.id_image}-small.jpg" alt="{$product.name|escape:'htmlall':'UTF-8'}" /></a>
                </td>
                <td class="cart_description">
                    <h5><a href="{$link->getProductLink($product.id_product, $product.link_rewrite)|escape:'htmlall':'UTF-8'}">{$product.name|escape:'htmlall':'UTF-8'}</a></h5>
                    {if $product.attributes}<a href="{$link->getProductLink($product.id_product, $product.link_rewrite)|escape:'htmlall':'UTF-8'}">{$product.attributes|escape:'htmlall':'UTF-8'}</a>{/if}
                </td>
                <td class="cart_ref">{if $product.reference}{$product.reference|escape:'htmlall':'UTF-8'}{else}--{/if}</td>
                <td class="cart_availability">
                    {if $product.active AND ($product.allow_oosp OR $product.stock_quantity > 0)}
                        <img src="{$img_dir}icon/available.gif" alt="{l s='Available'}" />
                    {else}
                        <img src="{$img_dir}icon/unavailable.gif" alt="{l s='Out of Stock'}" />
                    {/if}
                </td>
                <td class="cart_unit"><span class="price">{convertPrice price=$product.price}</span></td>
                <td class="cart_quantity">
                    <p>{$product.quantity|intval}</p>
                </td>
                <td class="cart_total"><span class="price" style="border-bottom: none;">{convertPrice price=$product.total}</span></td>
            </tr>
        {/foreach}
        </tbody>
    {if $discounts}
        <tbody>
        {foreach from=$discounts item=discount name=discountLoop}
            <tr class="cart_discount {if $smarty.foreach.discountLoop.last}last_item{elseif $smarty.foreach.discountLoop.first}first_item{else}item{/if}">
                <td class="cart_discount_name" colspan="2">{$discount.name}</td>
                <td class="cart_discount_description" colspan="3">{$discount.description}</td>
                <td class="cart_discount_delete"></td>
                <td class="cart_discount_price"><span class="price-discount">-{convertPrice price=$discount.value_real}</span></td>
            </tr>
        {/foreach}
        </tbody>
    {/if}
    </table>
</div>
</div>
{/if}

{if $invoice->id}
    <ul id="invoice_address" class="address item">
        <li class="address_title">{l s='Billing Address'}</li>
        {if $invoice->company}<li class="address_company">{$invoice->company|escape:'htmlall':'UTF-8'}</li>{/if}
        <li class="address_name">{$invoice->firstname|escape:'htmlall':'UTF-8'} {$invoice->lastname|escape:'htmlall':'UTF-8'}</li>
        <li class="address_address1">{$invoice->address1|escape:'htmlall':'UTF-8'}</li>
        {if $invoice->address2}<li class="address_address2">{$invoice->address2|escape:'htmlall':'UTF-8'}</li>{/if}
    <li class="address_city">{$invoice->city|escape:'htmlall':'UTF-8'}&nbsp; {$inv_state_name|escape:'htmlall':'UTF-8'}    {$invoice->postcode|escape:'htmlall':'UTF-8'}</li>
        <li class="address_country">{$invoice->country|escape:'htmlall':'UTF-8'}</li>
        <b><li class="address_update"><a  href="{$base_dir_ssl}address.php?id_address={$invoice->id|intval}&amp;back=modules/payauthorizenet/payment.php" title="{l s='Edit'}">{l  s='Edit'}</a></li></b>
    <li>NOTE: Please ensure your Billing Address matches the address on your Credit Card statement.</li>
    </ul>
    {/if}

<ul id="address_delivery" class="address alternate_item">
    <li class="address_title">{l s="Credit Card Information"}</li>
    <li>{$cardName}</li>
    <li>{$cardNumberDisplay}</li>
    <li>{$cardExpires}</li>
    <li>{$cardCode}</li>
    <li></li>
</ul>
<form action="{$self}" method="post" class="std">
<input type="hidden" name="cardName" value="{$cardName}" />
<input type="hidden" name="cardNumber" value="{$cardNumber}" />
<input type="hidden" name="cardExpires" value="{$cardExpires}" />
<input type="hidden" name="expMonth" value="{$expMonth}" />
<input type="hidden" name="expYear" value="{$expYear}" />
<input type="hidden" name="cardCode" value="{$cardCode}" />

<p class="cart_navigation">
    <a href="{$base_dir_ssl}modules/payauthorizenet/payment.php" class="button">&laquo; {l s='Previous' mod='payauthorizenet'}</a>
    <input type="submit" name="submitPayment" value="{l s='Place Order' mod='payauthorizenet'} &raquo;" class="exclusive_large" />
</p>
</form>
<br /><br/><br /><br/>

```
payauthorizenet.php:

```
<?php
/**
 * Authorize.net payment module processor
 *
 * @author Geoff Woodburn [http://www.woodburndesigns.com]
 * @author Jesse Hemingway [http://www.jirosoft.net]
 * @version 0.91
 */


class PayAuthorizeNet extends PaymentModule
{
    private    $_html = '';
    private $_postErrors = array();
    private $_responseReasonText = null;

    public function __construct()
    {
        $this->name = 'payauthorizenet';
        $this->tab = 'Payment';
        $this->version = '1.0';

        parent::__construct();

        /* The parent construct is required for translations */
        $this->page = basename(__FILE__, '.php');
        $this->displayName = $this->l('Credit Card');
        $this->description = $this->l('Accepts payments by Credit Card via Authorize.Net');
    }

    public function getAuthNetUrl()
    {
            return Configuration::get('AUTHORIZENET_SANDBOX') ? 'https://test.authorize.net/gateway/transact.dll' : 'https://secure.authorize.net/gateway/transact.dll';
    }

    public function install()
    {
        if (!parent::install() OR
            !Configuration::updateValue('AUTHORIZENET_ID', 'your-authorize.net-login-id') OR
            !Configuration::updateValue('AUTHORIZENET_TRANSKEY', 'your-authorize.net-transaction-key') OR
            !Configuration::updateValue('AUTHORIZENET_SANDBOX', 1) OR
            !Configuration::updateValue('AUTHORIZENET_CURRENCY', 'prestashop') OR
            !Configuration::updateValue('AUTHORIZENET_USEPROXY', 0) OR
            !Configuration::updateValue('AUTHORIZENET_PROXY', '')
            OR !$this->registerHook('payment'))
            return false;
        return true;
    }

    public function uninstall()
    {
        if (!Configuration::deleteByName('AUTHORIZENET_ID') OR
            !Configuration::deleteByName('AUTHORIZENET_TRANSKEY') OR
            !Configuration::deleteByName('AUTHORIZENET_SANDBOX') OR
            !Configuration::deleteByName('AUTHORIZENET_CURRENCY') OR
            !Configuration::deleteByName('AUTHORIZENET_USEPROXY') OR
            !Configuration::deleteByName('AUTHORIZENET_PROXY') OR
            !parent::uninstall())
            return false;
        return true;
    }

    public function getContent()
    {
        $this->_html = '<h2>Authorize.net</h2>';
        if (isset($_POST['submitAuthNet']))
        {
            if (empty($_POST['loginID']))
                $this->_postErrors[] = $this->l('Authorize.net login ID is required.');
            if (empty($_POST['transKey']))
                $this->_postErrors[] = $this->l('Authorize.net transaction key is required.');
            if (!isset($_POST['sandbox']))
                $_POST['sandbox'] = 1;
            if (!isset($_POST['useProxy']))
                $_POST['useProxy'] = 0;
            if ($_POST['useProxy'] && empty($_POST['proxy']))
                $this->_postErrors[] = $this->l('Proxy server url or ip required for proxied transactions.');
            if (empty($_POST['currency']))
                $_POST['currency'] = 'customer';
            if (!sizeof($this->_postErrors))
            {
                Configuration::updateValue('AUTHORIZENET_ID', $_POST['loginID']);
                Configuration::updateValue('AUTHORIZENET_TRANSKEY', $_POST['transKey']);
                Configuration::updateValue('AUTHORIZENET_SANDBOX', intval($_POST['sandbox']));
                Configuration::updateValue('AUTHORIZENET_CURRENCY', $_POST['currency']);
                Configuration::updateValue('AUTHORIZENET_USEPROXY', $_POST['useProxy']);
                Configuration::updateValue('AUTHORIZENET_PROXY', $_POST['proxy']);
                $this->displayConf();
            }
            else
                $this->displayErrors();
        }

        $this->displayAuthNet();
        $this->displayFormSettings();
        return $this->_html;
    }

    public function displayConf()
    {
        $this->_html .= '
        <div class="conf confirm">
            <img src="../img/admin/ok.gif" alt="'.$this->l('Confirmation').'" />
            '.$this->l('Settings updated').'
        </div>';
    }

    public function displayErrors()
    {
        $nbErrors = sizeof($this->_postErrors);
        $this->_html .= '
        <div class="alert error">
            <h3>'.($nbErrors > 1 ? $this->l('There are') : $this->l('There is')).' '.$nbErrors.' '.($nbErrors > 1 ? $this->l('errors') : $this->l('error')).'</h3>
            <ol>';
        foreach ($this->_postErrors AS $error)
            $this->_html .= '<li>'.$error.'</li>';
        $this->_html .= '
            </ol>
        </div>';
    }


    public function displayAuthNet()
    {
        $this->_html .= '
        <img src="../modules/payauthorizenet/authorizenet.gif" style="float:left; padding: 10px 0px; margin-right:15px;" />
        <b>'.$this->l('This module allows you to accept payments by Authorize.net.').'</b><br /><br />
        '.$this->l('If the client chooses this payment mode, your Authorize.net account will be automatically credited.').'<br />
        '.$this->l('You need to configure your Authorize.net account first before using this module.').'
        <br /><br /><br />';
    }

    public function displayFormSettings()
    {
        $conf = Configuration::getMultiple(array('AUTHORIZENET_ID',
                                                'AUTHORIZENET_TRANSKEY',
                                                'AUTHORIZENET_SANDBOX',
                                                'AUTHORIZENET_CURRENCY',
                                                'AUTHORIZENET_USEPROXY',
                                                'AUTHORIZENET_PROXY'));
        $loginID = array_key_exists('loginID', $_POST) ? $_POST['loginID'] : (array_key_exists('AUTHORIZENET_ID', $conf) ? $conf['AUTHORIZENET_ID'] : '');
        $transKey = array_key_exists('transkey', $_POST) ? $_POST['transKey'] : (array_key_exists('AUTHORIZENET_TRANSKEY', $conf) ? $conf['AUTHORIZENET_TRANSKEY'] : '');
        $sandbox = array_key_exists('sandbox', $_POST) ? $_POST['sandbox'] : (array_key_exists('AUTHORIZENET_SANDBOX', $conf) ? $conf['AUTHORIZENET_SANDBOX'] : '');
        $useProxy = array_key_exists('useProxy', $_POST) ? $_POST['useProxy'] : (array_key_exists('AUTHORIZENET_USEPROXY', $conf) ? $conf['AUTHORIZENET_USEPROXY'] : '');
        $proxy = array_key_exists('proxy', $_POST) ? $_POST['proxy'] : (array_key_exists('AUTHORIZENET_PROXY', $conf) ? $conf['AUTHORIZENET_PROXY'] : '');
        $currency = array_key_exists('currency', $_POST) ? $_POST['currency'] : (array_key_exists('AUTHORIZENET_CURRENCY', $conf) ? $conf['AUTHORIZENET_CURRENCY'] : 'prestashop');

        $this->_html .= '
        <form action="'.$_SERVER['REQUEST_URI'].'" method="post">
        <fieldset>
            <legend><img src="../img/admin/contact.gif" />'.$this->l('Settings').'</legend>
            <label>'.$this->l('Authorize.net login ID').'</label>
            <div class="margin-form"><input type="text" size="38" name="loginID" value="'.htmlentities($loginID, ENT_COMPAT, 'UTF-8').'" /></div>
            <label>'.$this->l('Authorize.net transaction key').'</label>
            <div class="margin-form"><input type="text" size="38" name="transKey" value="'.htmlentities($transKey, ENT_COMPAT, 'UTF-8').'" /></div>
            <label>'.$this->l('Sandbox mode').'</label>
            <div class="margin-form">
                <input type="radio" name="sandbox" value="1" '.($sandbox ? 'checked="checked"' : '').' /> '.$this->l('Yes').'
                <input type="radio" name="sandbox" value="0" '.(!$sandbox ? 'checked="checked"' : '').' /> '.$this->l('No').'
            </div>
            <label>'.$this->l('Use proxy').'</label>
            <div class="margin-form">
                <input type="radio" name="useProxy" value="1" '.($useProxy ? 'checked="checked"' : '').' /> '.$this->l('Yes').'
                <input type="radio" name="useProxy" value="0" '.(!$useProxy ? 'checked="checked"' : '').' /> '.$this->l('No').'
            </div>
            <label>'.$this->l('Proxy url or IP').'</label>
            <div class="margin-form"><input type="text" size="38" name="proxy" value="'.htmlentities($proxy, ENT_COMPAT, 'UTF-8').'" /></div>
            <label>'.$this->l('Currency').'</label>
            <div class="margin-form">
                <input type="radio" name="currency" value="prestashop" '.($currency == 'prestashop' ? 'checked="checked"' : '').' /> '.$this->l('Use PrestaShop currency').'
                <br /><input type="radio" name="currency" value="customer" '.($currency == 'customer' ? 'checked="checked"' : '').' /> '.$this->l('Use customer currency').'
            </div>
            <br /><center><input type="submit" name="submitAuthNet" value="'.$this->l('Update settings').'" class="button" /></center>
        </fieldset>
        </form><br /><br />
        <fieldset class="width3">
            <legend><img src="../img/admin/warning.gif" />'.$this->l('Information').'</legend>
            '.$this->l('In order to use your Authorize.net payment module, you have to configure your Authorize.net account (sandbox account as well as live account). Log in to Authorize.net and follow these instructions.').'<br /><br />INSTRUCTIONS TO COME!'.'
        </fieldset>';
    }

    public function hookPayment($params)
    {
        global $smarty;

        $address = new Address(intval($params['cart']->id_address_invoice));
        $customer = new Customer(intval($params['cart']->id_customer));

        if (Configuration::get('AUTHORIZENET_CURRENCY') == 'customer')
            $id_currency = intval($params['cart']->id_currency);
        else
            $id_currency = intval(Configuration::get('PS_CURRENCY_DEFAULT'));

        $currency = new Currency(intval($id_currency));

        if (!Validate::isLoadedObject($address) OR !Validate::isLoadedObject($customer) OR
            !Validate::isLoadedObject($currency))
            return $this->l('Authorize.net error: (invalid address or customer)');

        $smarty->assign(array(
            'this_path' => $this->_path,
            'this_path_ssl' => (Configuration::get('PS_SSL_ENABLED') ? 'https://' : 'https://').htmlspecialchars($_SERVER['HTTP_HOST'], ENT_COMPAT, 'UTF-8').__PS_BASE_URI__.'modules/'.$this->name.'/'
        ));

        return $this->display(__FILE__, 'payauthorizenet.tpl');
    }

    public function getL($key)
    {
        $translations = array(
            'mc_gross' => $this->l('Paypal key \'mc_gross\' not specified, can\'t control amount paid.'),
            'payment_status' => $this->l('Paypal key \'payment_status\' not specified, can\'t control payment validity'),
            'payment' => $this->l('Payment: '),
            'custom' => $this->l('Paypal key \'custom\' not specified, can\'t rely to cart'),
            'txn_id' => $this->l('Paypal key \'txn_id\' not specified, transaction unknown'),
            'mc_currency' => $this->l('Paypal key \'mc_currency\' not specified, currency unknown'),
            'cart' => $this->l('Cart not found'),
            'order' => $this->l('Order has already been placed'),
            'transaction' => $this->l('Paypal Transaction ID: '),
            'verified' => $this->l('PayPal payment not set to VERIFIED but:'),
            'connect' => $this->l('Impossible to connect to PayPal server')
        );
        return $translations[$key];
    }

    /**
     * Used outside of the payment hook to populate smarty vars
     *
     */
    public function populatePaymentVars()
    {
        global $smarty, $cart, $cookie;

        $address = new Address(intval($cart->id_address_invoice));
        $addressShip = new Address(intval($cart->id_address_delivery));
        $state = new State(intval($address->id_state));
        $address->state = $state->name;
        $state = new State(intval($addressShip->id_state));
        $addressShip->state = $state->name;

        $customer = new Customer(intval($cookie->id_customer));
        $this->loginID = Configuration::get('AUTHORIZENET_ID');
        $this->transKey = Configuration::get('AUTHORIZENET_TRANSKEY');
        $this->useProxy = Configuration::get('AUTHORIZENET_USEPROXY');
        $this->proxy = Configuration::get('AUTHORIZENET_PROXY');

        if (Configuration::get('AUTHORIZENET_CURRENCY') == 'customer')
            $id_currency = intval($cart->id_currency);
        else
            $id_currency = intval(Configuration::get('PS_CURRENCY_DEFAULT'));
        $this->currency = new Currency(intval($id_currency));

        $this->products = $cart->getProducts();


        foreach ($this->products as $key => $product)
        {
            $this->products[$key]['name'] = str_replace('"', '\'', $product['name']);
            if (isset($product['attributes']))
                $this->products[$key]['attributes'] = str_replace('"', '\'', $product['attributes']);
            $this->products[$key]['name'] = htmlentities(utf8_decode($product['name']));
            $this->products[$key]['authNetAmount'] = number_format(Tools::convertPrice($product['price_wt'], $this->currency), 2, '.', '');
        }
        $smarty->assign(array(
            'address' => $address,
            'addressShip' => $addressShip,
            'country' => new Country(intval($address->id_country)),
            'customer' => $customer,
            'loginID' => $this->loginID,
            'transKey' => $this->transKey,
            'currency' => $this->currency,
            'authNetUrl' => $this->getAuthNetUrl(),
            'amount' => number_format(Tools::convertPrice($cart->getOrderTotal(true, 4), $this->currency), 2, '.', ''),
            'shipping' =>  number_format(Tools::convertPrice($cart->getOrderShippingCost(), $this->currency), 2, '.', ''),
            'discounts' => $cart->getDiscounts(),
            'products' => $this->products,
            'total' => number_format(Tools::convertPrice($cart->getOrderTotal(true, 3), $this->currency), 2, '.', ''),
            'cartID' => intval($cart->id),
            'goBackUrl' => 'https://'.htmlspecialchars($_SERVER['HTTP_HOST'], ENT_COMPAT, 'UTF-8').__PS_BASE_URI__.'order-confirmation.php?key='.$customer->secure_key,
            'returnUrl' => 'https://'.htmlspecialchars($_SERVER['HTTP_HOST'], ENT_COMPAT, 'UTF-8').__PS_BASE_URI__.'modules/payauthorizenet/validation.php',
            'this_path' => $this->_path
        ));
    }

    /**
     * Try to complete the order in the cart
     *
     * @result string See handleCurlResponse for details
     */
    public function makeCurlRequest()
    {
        global $smarty;

        if (Order::getOrderByCartId($smarty->get_template_vars('cartID')))
            return 'duplicate';

        $authValues = array    (
            // merchant variables
            "x_login" => $this->loginID,
            "x_tran_key" => $this->transKey,

            // transaction variables
            "x_version" => "3.1",
            "x_type" => "AUTH_CAPTURE",
            "x_method" => "CC",
            "x_amount" => $smarty->get_template_vars('total'),
            "x_card_num" => $_POST['cardNumber'],
            "x_exp_date" => $_POST['cardExpires'],
            "x_card_code" => $_POST['cardCode'],
            "x_test_request" => Configuration::get('AUTHORIZENET_SANDBOX'),

            // order information
            "x_invoice_num" => $smarty->get_template_vars('cartID'),

            // customer information
            "x_first_name" => $smarty->get_template_vars('address')->firstname,
            "x_last_name" => $smarty->get_template_vars('address')->lastname,
            "x_company" => $smarty->get_template_vars('address')->company,
            "x_address" => $smarty->get_template_vars('address')->address1 . "\n" .
                            $smarty->get_template_vars('address')->address2,
            "x_city" => $smarty->get_template_vars('address')->city,
            "x_state" => $smarty->get_template_vars('address')->state,
            "x_zip" => $smarty->get_template_vars('address')->postcode,
            "x_country" => $smarty->get_template_vars('address')->country,
            "x_email" => $smarty->get_template_vars('customer')->email,
            "x_cust_id" => $smarty->get_template_vars('customer')->id,

            // shipping information
            "x_ship_to_first_name" => $smarty->get_template_vars('addressShip')->firstname,
            "x_ship_to_last_name" => $smarty->get_template_vars('addressShip')->lastname,
            "x_ship_to_company" => $smarty->get_template_vars('addressShip')->company,
            "x_ship_to_address" => $smarty->get_template_vars('addressShip')->address1 . "\n" .
                            $smarty->get_template_vars('addressShip')->address2,
            "x_ship_to_city" => $smarty->get_template_vars('addressShip')->city,
            "x_ship_to_state" => $smarty->get_template_vars('addressShip')->state,
            "x_ship_to_zip" => $smarty->get_template_vars('addressShip')->postcode,
            "x_ship_to_country" => $smarty->get_template_vars('addressShip')->country,

            // response formatting
            "x_delim_char" => "|",
            "x_delim_data" => "TRUE",
        );
        $fields = http_build_query($authValues);


        // perform request
        $ch = curl_init($this->getAuthNetUrl());
        curl_setopt($ch, CURLOPT_HEADER, 0); // set to 0 to eliminate header info from response
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1); // Returns response data instead of TRUE(1)
        curl_setopt($ch, CURLOPT_POSTFIELDS, $fields); // use HTTP POST to send form data
        curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
error_log("Proxy setup (use: $this->useProxy) (url: $this->proxy)");
        if ($this->useProxy) {
            curl_setopt($ch, CURLOPT_HTTPPROXYTUNNELL, true);
            curl_setopt($ch, CURLOPT_PROXYTYPE, CURLPROXY_HTTP);
            curl_setopt($ch, CURLOPT_PROXY, $this->proxy);
        }
error_log("Sending request to " . $this->getAuthNetUrl() . ":\n" . $fields);
        $response = curl_exec($ch); //execute post and get results
        if (!$response)
            return "cURL error: " . curl_error($ch);

error_log($response);
        curl_close ($ch);

        return $this->handleCurlResponse($response);
    }

    /**
     * Handle the authorize.net curl response
     *
     * @param string $response Raw cURL gateway response
     * @result string Standard response term OR error string if unknown; Terms:
     *        accepted - Card has been accepted and Order processed/validated successfully
     *        declined - Card has been declined
     *        amount - Order amount invalid
     *        invalid - Card info is invalid or expired
     *        duplicate - Duplicate transaction attempt
     *        merchant - Merchant id/transkey is invalid
     *        cardtype - Merchant does not accept this card type
     *        retry - Gateway asks that the transaction be reattempted later
     *        exception - Unknown gateway exception
     */
    private function handleCurlResponse($response)
    {
        global $smarty;

        $fieldNames = array('responseCode', 'responseSubCode', 'responseReasonCode', 'responseReasonText',
                            'authCode', 'avsCode', 'transactionID', 'invoiceNumber', 'description', 'amount',
                            'method', 'transType', 'customerID');
        for ($i = 13; $i < 38; $i++)
            $fieldNames[] = $i;
        $fieldNames = array_merge($fieldNames, array('cardCodeResponse', 'cardAuthResponse'));

        $fields = explode('|', $response);
        $nFieldsResponse = count($fields);
        for ($i = 40; $i < $nFieldsResponse; $i++)
            $fieldNames[] = $i;    // fill names array to match response fields

        if ($fields = @array_combine($fieldNames, $fields)) {
            if ($fields['responseCode'] == 1)
                return $this->finalizeOrder($fields['invoiceNumber'], $fields['amount'], $fields['transactionID']);
            if ($fields['responseCode'] == 4)
                return 'held';

            switch ($fields['responseReasonCode']) {
                case 2: case 3: case 4: case 41: case 44: case 45:
                    return 'declined';
                case 5:
                    return 'amount';
                case 6: case 7: case 8: case 27: case 37:
                    return 'invalid';
                case 11:
                    return 'duplicate';
                case 13: case 30: case 123:
                    return 'merchant';
                case 17: case 28:
                    return 'cardtype';
                case 19: case 20: case 21: case 22: case 23: case 25: case 26:
                    return 'retry';
                default:
                    $this->_responseReasonText = $fields['responseReasonText'] . "({$fields['responseReasonCode']})";
                    return $fields['responseReasonText'];
            }
        }

        return 'exception';        // gateway exception
    }

    /**
     * Attempts to finalize an accepted transaction
     *
     * @result string Should be 'accepted' unless something has gone quite wrong
     */
    public function finalizeOrder($cartID, $amount, $transactionID)
    {
        global $smarty;

        $cart = new Cart(intval($cartID));
        if (!$cart->id)
            return $this->l('Cart not found');
        if (Order::getOrderByCartId($smarty->get_template_vars('cartID')))
            return $this->l('Order has already been placed');

        $this->validateOrder($cartID, _PS_OS_PAYMENT_, $amount, $this->displayName, $this->l('Credit Card Transaction ID: ') . $transactionID);

        return 'accepted';
    }

    public function getResponseReasonText()
    {
        return $this->_responseReasonText;
    }


}

?>

```
payauthorizenet.tpl:

```
<p class="payment_module">
    <a href="{$this_path_ssl}payment.php" title="{l s='Pay with Credit Card' mod='payauthorizenet'}">
        <img src="{$module_dir}creditcard.gif" alt="{l s='Pay with Credit Card' mod='payauthorizenet'}" />
        {l s='Pay with Credit Card' mod='payauthorizenet'}
    </a>
</p>
```
payment.php:

```
<?php
/**
 * Authorize.net payment module controller
 *
 * @author Geoff Woodburn [http://www.woodburndesigns.com]
 * @author Jesse Hemingway [http://www.jirosoft.net]
 * @version 0.91
 */


/* SSL Management */
$useSSL = true;
$confirm = FALSE;

include(dirname(__FILE__).'/../../config/config.inc.php');
include(dirname(__FILE__).'/../../header.php');
include(dirname(__FILE__).'/payauthorizenet.php');

if (!$cookie->isLogged())
    Tools::redirect('authentication.php?back=order.php');

$payAuthorize = new PayAuthorizenet();
$payAuthorize->populatePaymentVars();


/* Manage Discounts from ORDER.PHP */

    if ((Tools::isSubmit('submitDiscount') OR isset($_GET['submitDiscount'])) AND Tools::getValue('discount_name'))
    {
        $discountName = Tools::getValue('discount_name');
        if (!Validate::isDiscountName($discountName))
            $errors[] = Tools::displayError('Coupon Code Not Valid!');
        else
        {
            $discount = new Discount(intval(Discount::getIdByName($discountName)));
            if (is_object($discount) AND $discount->id)
            {
                if ($tmpError = $cart->checkDiscountValidity($discount, $cart->getDiscounts(), $cart->getOrderTotal(), $cart->getProducts(), true))
                    $errors[] = $tmpError;
            }
            else
                $errors[] = Tools::displayError('Coupon Code Not Valid!');
            if (!sizeof($errors))
            {
                $cart->addDiscount(intval($discount->id));
        Tools::redirect('../modules/payauthorizenet/payment.php');
            }
            else
            {
                $smarty->assign(array(
                    'errors' => $errors,
                    'discount_name' => Tools::safeOutput($discountName)));
            }
        }
    }
    elseif (isset($_GET['deleteDiscount']) AND Validate::isUnsignedId($_GET['deleteDiscount']))
    {
        $cart->deleteDiscount(intval($_GET['deleteDiscount']));
        Tools::redirect('../modules/payauthorizenet/payment.php');
    }

if (Tools::isSubmit('nextPayment'))
{
    $cardName = trim(Tools::getValue('cardName'));
    if(empty($cardName))
        $errors[] = Tools::displayError('The name as it appears on the card is required');
    $cardNumber = trim(Tools::getValue('cardNumber'));
    if(empty($cardNumber))
        $errors[] = Tools::displayError('The credit card number is required');
    $cardCode = trim(Tools::getValue('cardCode'));
    if(empty($cardCode))
        $errors[] = Tools::displayError('The cvn on the back of the credit card is required');
    $expMonth = trim(Tools::getValue('expMonth'));
    if(empty($expMonth))
        $errors[] = Tools::displayError('The month your credit card expires is required');
    $expYear = trim(Tools::getValue('expYear'));
    if(empty($expYear))
        $errors[] = Tools::displayError('The year your credit card expires is required');
    if(!empty($expMonth) && !empty($expYear))
        $cardExpires = $expMonth. "/" .$expYear;
    $smarty->assign('errors', $errors);
    if(empty($errors))
        $confirm = TRUE;
} else if(Tools::isSubmit('submitPayment')){
    $cardName = trim(Tools::getValue('cardName'));
    $cardNumber = trim(Tools::getValue('cardNumber'));
    $cardCode = trim(Tools::getValue('cardCode'));
    $cardExpires = trim(Tools::getValue('cardExpires'));
    $expMonth = trim(Tools::getValue('expMonth'));
    $expYear = trim(Tools::getValue('expYear'));
    $response = $payAuthorize->makeCurlRequest();
    global $cookie;
    $contactEmails = Contact::getContacts(intval($cookie->id_lang));

    switch($response){
        case 'accepted':
            Tools::redirect('thank-you.php', _MODULE_DIR_.'payauthorizenet/');
            break;
        case 'declined':
            $errors[] = Tools::displayError('We are sorry, your credit card has been
            declined. Please contact your credit card company for further details.');
            break;
        case 'amount':
            $errors[] = Tools::displayError('We are sorry, the order amount provided
            is invalid. Please check the details of your cart and try again.');
            break;
        case 'invalid':
            $errors[] = Tools::displayError('The information provided for the credit card
            is either invalid or the card has expired. Please try again.');
            break;
        case 'duplicate':
            $errors[] = Tools::displayError('The information provided for the credit card
            is either invalid or the card has expired. Please try again.');
            break;
        case 'merchant':
            Mail::Send(intval($cookie->id_lang), 'contact', 'Message from authorize.net module', array('{email}' => $contactEmails[0]['email'], '{message}' => 'This message is to notify you that the merchant id/transkey is invalid in your authorize.net payment module.'), $contactEmails[0]['email']);
            $errors[] = Tools::displayError('The shopping cart has yet to be setup
            properly by the merchant. We apologize for any inconvenience this may
            have caused.');
            break;
        case 'cardType':
            $errors[] = Tools::displayError('We are sorry, we do not accept the
            card type provided. Please try again.');
            break;
        case 'retry':
            $errors[] = Tools::displayError('We are experiencing technical difficulties.
            Please try again later.');
            break;
        case 'exception':
            $errors[] = Tools::displayError('An error has occured. We apologize for any
            inconvenience this may have caused.');
        default:
            Mail::Send(intval($cookie->id_lang), 'contact', 'Message from authorize.net module', array('{email}' => $contactEmails[0]['email'], '{message}' => 'This message is to notify you that the following error has occured in your authorize.net payment module: ' . $payAuthorize->getResponseReasonText()), $contactEmails[0]['email']);
            $errors[] = Tools::displayError('An error has occured. We apologize for any
            inconvenience this may have caused.');
    }
    $smarty->assign('errors', $errors);
}
function cardMonths()
{
    for ($i = 01; $i < 13; $i++)
        $tab[] = sprintf("%02d", $i);
    return $tab;
}

function cardYears()
{
    for ($i = date('Y'); $i < (date('Y') + 11); $i++)
        $tab[] = $i;
    return $tab;
}

$smarty->assign(array(
    'years' => cardYears(),
    'months' => cardMonths(),
));

    /* GET SHIPPING and BILLING STATE NAMES TO PUT IN ADDRESSES */
    
    $result_ship = Db::getInstance()->getrow('
        SELECT `id_state`
        FROM `'._DB_PREFIX_.'address`
        WHERE `id_address` = '.intval($cart->id_address_delivery));
    $ship_state=intval($result_ship['id_state']);

    $result_ship_state = Db::getInstance()->getrow('
        SELECT `name`
        FROM `'._DB_PREFIX_.'state`
        WHERE `id_state` = '.intval($ship_state));
    $ship_state_name=$result_ship_state['name'];

    $result_inv = Db::getInstance()->getrow('
        SELECT `id_state`
        FROM `'._DB_PREFIX_.'address`
        WHERE `id_address` = '.intval($cart->id_address_invoice));
    $inv_state=intval($result_inv['id_state']);

    $result_inv_state = Db::getInstance()->getrow('
        SELECT `name`
        FROM `'._DB_PREFIX_.'state`
        WHERE `id_state` = '.intval($inv_state));
        $inv_state_name=$result_inv_state['name'];


$summary = $cart->getSummaryDetails();
$smarty->assign($summary);
$smarty->assign(array(
    
    'ship_state_name' => $ship_state_name,
    'inv_state_name' => $inv_state_name,
    'token' => Tools::getToken(false),
    'express' => intval($cookie->express),
    'voucherAllowed' => Configuration::get('PS_VOUCHERS'),
    'HOOK_SHOPPING_CART' => Module::hookExec('shoppingCart', $summary),
    'shippingCost' => $cart->getOrderTotal(true, 5),
    'cardName' => $cardName,
    'cardNumberDisplay' => "xxxx-xxxx-xxxx-".substr($cardNumber, - 4),
    'cardNumber' => $cardNumber,
    'cardExpires' => $cardExpires,
    'expMonth' => $expMonth,
    'expYear' => $expYear,
    'cardCode' => $cardCode,
    'self' => $_SERVER['PHP_SELF']
));

if (file_exists(_PS_SHIP_IMG_DIR_.intval($cart->id_carrier).'.jpg'))
    $smarty->assign('carrierPicture', 1);

if(!$confirm)
    $smarty->display(dirname(__FILE__).'/payment.tpl');
else
    $smarty->display(dirname(__FILE__).'/confirm-payment.tpl');

include_once(dirname(__FILE__).'/../../footer.php');

?>
```payment.tpl:

```
{capture name=path}{l s='Credit Card Payment' mod='payauthorizenet'}{/capture}
{include file=$tpl_dir./breadcrumb.tpl}
<script language="javascript" src="{$this_path}popup.js"></script>

<h2>{l s='Credit Card Payment' mod='payauthorizenet'}</h2>

{assign var='current_step' value='payment'}

{include file=$tpl_dir./errors.tpl}

{*<h3>{l s='Credit Card Payment' mod='payauthorizenet'}</h3>*}

<form action="{$self}" method="post" id="account-creation_form" class="std">

<fieldset class="account_creation">
<center><h3>{l s='Payment Info'}</h3></center>
    <p class="required">
        <label for="cardName">{l s='Name on Card'}</label>
        <input type="text" id="cardName" name="cardName" value="{if isset($cardName)}{$cardName|escape:'htmlall'|stripslashes}{/if}" />
        <sup>*</sup>
    </p>
    <p class="required">
        <label for="cardNumber">{l s='Credit Card No.'}</label>
        <input type="text" id="cardNumber" name="cardNumber" value="{if isset($cardNumber)}{$cardNumber|escape:'htmlall'|stripslashes}{/if}" />
        <sup>*</sup>
    </p>
    <p class="required">
        <label for="expMonth">{l s='Expiration Date '}</label>
        <select id="expMonth" name="expMonth">
            <option value="">-</option>
            {foreach from=$months item=month}
                <option value="{$month}" {if ($expMonth == $month)} selected="selected"{/if}>{l s="$month"}</option>
            {/foreach}
        </select>
        <select id="expYear" name="expYear">
            <option value="">-</option>
                {foreach from=$years item=year}
                    <option value="{$year|escape:'htmlall':'UTF-8'}" {if ($expYear == $year)} selected="selected"{/if}>{$year|escape:'htmlall':'UTF-8'}</option>
                {/foreach}
        </select>
        <sup>*</sup>
    </p>
    <p class="required">
        <label for="cardCode">{l s='CVN'}</label>
        <input type="text" id="cardCode" name="cardCode" value="{if isset($cardCode)}{$cardCode|escape:'htmlall'|stripslashes}{/if}" />
<sup>*</sup>
<a href='{$this_path}CVC.jpg' class="popup" target="_blank">Where Is My CVN?</a>
</p>

<center>
<p class="required">
<sup>* Required</sup></p></center>
<b><center>** You may review and confirm your Order after clicking "Continue"</center></b>
</fieldset>

    <p class="cart_navigation">
        <a href="{$base_dir_ssl}{if $express==1}express-order.php?step=3#payment{else}order.php?step=3{/if}" class="button">&laquo; {l s='Previous' mod='payauthorizenet'}</a>
        <input type="submit" name="nextPayment" value="{l s='Continue' mod='payauthorizenet'} &raquo;" class="exclusive_large" />
    </p>
</form>
<br /><br/>

```thank-you.php:

```
<?php
/**
 * Authorize.net payment module thank-you page
 *
 * @author Geoff Woodburn [http://www.woodburndesigns.com]
 * @author Jesse Hemingway [http://www.jirosoft.net]
 * @version 0.91
 */


/* SSL Management */
$useSSL = true;

include(dirname(__FILE__).'/../../config/config.inc.php');
include(dirname(__FILE__).'/../../header.php');

if (!$cookie->isLogged())
    Tools::redirect('authentication.php?back=order.php');

$smarty->display(dirname(__FILE__).'/thank-you.tpl');

include_once(dirname(__FILE__).'/../../footer.php');

?>
```thank-you.tpl:

```
{capture name=path}{l s='Payment'}{/capture}
{include file=$tpl_dir./breadcrumb.tpl}

<h2>{l s='Thank You For Your Order!'}</h2>

{assign var='current_step' value='payment'}
{include file=$tpl_dir./order-steps.tpl}

<h3>Your Order Has Been Processed.</h3><br>
<p>Thank You For Your Purchase! We Have Successfully Processed Your Order</p>
<p>If You Would Like To View Your Order History Please <a href=history.php>Click Here!</a></p>
```

---

