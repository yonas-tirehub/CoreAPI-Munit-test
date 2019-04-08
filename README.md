# CoreAPI-Munit-test
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Inventory_POST.xml
===============================
<?xml version="1.0" encoding="UTF-8"?>
<mule xmlns="http://www.mulesoft.org/schema/mule/core" xmlns:doc="http://www.mulesoft.org/schema/mule/documentation" xmlns:munit="http://www.mulesoft.org/schema/mule/munit" xmlns:spring="http://www.springframework.org/schema/beans" xmlns:core="http://www.mulesoft.org/schema/mule/core" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.mulesoft.org/schema/mule/munit http://www.mulesoft.org/schema/mule/munit/current/mule-munit.xsd
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-current.xsd
http://www.mulesoft.org/schema/mule/core http://www.mulesoft.org/schema/mule/core/current/mule.xsd">
    <munit:config doc:name="Munit configuration" mock-connectors="false" mock-inbounds="false"/>
    <spring:beans>
        <spring:import resource="classpath:interface.xml"/>
         <spring:import resource="classpath:orders-implementation.xml"/>
        <spring:import resource="classpath:global.xml"/>
        <spring:import resource="classpath:error-handling.xml"/>
        <spring:import resource="classpath:poll-tirehub-cache-auth-token-refresh.xml"/>
        <spring:import resource="classpath:brandmodelinfo.xml"/>
        <spring:import resource="classpath:locationinfo.xml"/>
        <spring:import resource="classpath:lookupcommondealers.xml"/>
        <spring:import resource="classpath:lookupinvoices.xml"/>
        <spring:import resource="classpath:physicalinvoices.xml"/>
        <spring:import resource="classpath:poll-auth-token-refresh.xml"/>
        <spring:import resource="classpath:ecommerceiteminfo.xml"/>
        <spring:import resource="classpath:inventory-check-implementation.xml"/>
    </spring:beans>
    <munit:test name="_postInventoryCoreAPItest-post:/inventory:application/json:CoreAPI-configTest" description="Test">
        <munit:set payload="#[getResource('sample_data/invent.json').asString()]" doc:name="Set Message" mimeType="application/json"/>
        <flow-ref name="post:/inventory:application/json:CoreAPI-config" doc:name="Flow-ref to post:/inventory:application/json:CoreAPI-config"/>
        <munit:assert-not-null doc:name="Assert Not Null Payload"/>
    </munit:test>
</mule>

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Inventory_GET.xml
====================


<?xml version="1.0" encoding="UTF-8"?>
<mule xmlns:mock="http://www.mulesoft.org/schema/mule/mock" xmlns:dw="http://www.mulesoft.org/schema/mule/ee/dw" xmlns="http://www.mulesoft.org/schema/mule/core" xmlns:doc="http://www.mulesoft.org/schema/mule/documentation" xmlns:munit="http://www.mulesoft.org/schema/mule/munit" xmlns:spring="http://www.springframework.org/schema/beans" xmlns:core="http://www.mulesoft.org/schema/mule/core" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.mulesoft.org/schema/mule/munit http://www.mulesoft.org/schema/mule/munit/current/mule-munit.xsd
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-current.xsd
http://www.mulesoft.org/schema/mule/core http://www.mulesoft.org/schema/mule/core/current/mule.xsd
http://www.mulesoft.org/schema/mule/ee/dw http://www.mulesoft.org/schema/mule/ee/dw/current/dw.xsd
http://www.mulesoft.org/schema/mule/mock http://www.mulesoft.org/schema/mule/mock/current/mule-mock.xsd">
   <munit:config doc:name="Munit configuration" mock-connectors="false" mock-inbounds="false"/>
    <spring:beans>
        <spring:import resource="classpath:interface.xml"/>
         <spring:import resource="classpath:orders-implementation.xml"/>
        <spring:import resource="classpath:global.xml"/>
        <spring:import resource="classpath:error-handling.xml"/>
        <spring:import resource="classpath:poll-tirehub-cache-auth-token-refresh.xml"/>
        <spring:import resource="classpath:brandmodelinfo.xml"/>
        <spring:import resource="classpath:locationinfo.xml"/>
        <spring:import resource="classpath:lookupcommondealers.xml"/>
        <spring:import resource="classpath:lookupinvoices.xml"/>
        <spring:import resource="classpath:physicalinvoices.xml"/>
        <spring:import resource="classpath:poll-auth-token-refresh.xml"/>
        <spring:import resource="classpath:ecommerceiteminfo.xml"/>
        <spring:import resource="classpath:inventory-check-implementation.xml"/>
    </spring:beans>
   
    <munit:test name="Inventory-GET-suite-get:/inventory:CoreAPI-configTest" description="Test">
        <munit:set payload="#[]" doc:name="Set Message">
            <munit:inbound-properties>
                <munit:inbound-property key="http.query.params" value="#[{&quot;dealerCode&quot;: &quot;302812&quot;,&quot;itemId&quot;:&quot;BR 007223&quot;,&quot;brand&quot;: &quot;BRIDGESTONE&quot;,&quot;model&quot;: &quot;ECOPIA EP422+&quot;,&quot;tireSize&quot;: &quot;205/60R16&quot;,&quot;width&quot;: &quot;205&quot;,&quot;rimDiameter&quot;: &quot;16&quot;}]"/>
            </munit:inbound-properties>
        </munit:set>
        <flow-ref name="get:/inventory:CoreAPI-config" doc:name="Flow-ref to get:/inventory:CoreAPI-config"/>
        <munit:assert-not-null doc:name="Assert Not Null Payload"/>
    </munit:test>
   
</mule>
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
order_POST.xml
==================

<?xml version="1.0" encoding="UTF-8"?>
<mule xmlns="http://www.mulesoft.org/schema/mule/core" xmlns:doc="http://www.mulesoft.org/schema/mule/documentation" xmlns:munit="http://www.mulesoft.org/schema/mule/munit" xmlns:spring="http://www.springframework.org/schema/beans" xmlns:core="http://www.mulesoft.org/schema/mule/core" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.mulesoft.org/schema/mule/munit http://www.mulesoft.org/schema/mule/munit/current/mule-munit.xsd
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-current.xsd
http://www.mulesoft.org/schema/mule/core http://www.mulesoft.org/schema/mule/core/current/mule.xsd">
   <munit:config doc:name="Munit configuration" mock-connectors="false" mock-inbounds="false"/>
    <spring:beans>
        <spring:import resource="classpath:interface.xml"/>
         <spring:import resource="classpath:orders-implementation.xml"/>
        <spring:import resource="classpath:global.xml"/>
        <spring:import resource="classpath:error-handling.xml"/>
        <spring:import resource="classpath:poll-tirehub-cache-auth-token-refresh.xml"/>
        <spring:import resource="classpath:brandmodelinfo.xml"/>
        <spring:import resource="classpath:locationinfo.xml"/>
        <spring:import resource="classpath:lookupcommondealers.xml"/>
        <spring:import resource="classpath:lookupinvoices.xml"/>
        <spring:import resource="classpath:physicalinvoices.xml"/>
        <spring:import resource="classpath:poll-auth-token-refresh.xml"/>
        <spring:import resource="classpath:ecommerceiteminfo.xml"/>
        <spring:import resource="classpath:inventory-check-implementation.xml"/>
    </spring:beans>
    <munit:test name="order_POST-post:/order:application/json:CoreAPI-configTest" description="Test">
        <munit:set payload="#[getResource('sample_data/order.json').asString()]" mimeType="application/json" doc:name="Set Message"/>
        <flow-ref name="post:/order:application/json:CoreAPI-config" doc:name="Flow-ref to post:/order:application/json:CoreAPI-config"/>
        <munit:assert-not-null doc:name="Assert Not Null Payload"/>
    </munit:test>
</mule>
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
ordernNo_dealerCode_URI_GET.xml
====================================
<?xml version="1.0" encoding="UTF-8"?>
<mule xmlns="http://www.mulesoft.org/schema/mule/core" xmlns:doc="http://www.mulesoft.org/schema/mule/documentation" xmlns:munit="http://www.mulesoft.org/schema/mule/munit" xmlns:spring="http://www.springframework.org/schema/beans" xmlns:core="http://www.mulesoft.org/schema/mule/core" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.mulesoft.org/schema/mule/munit http://www.mulesoft.org/schema/mule/munit/current/mule-munit.xsd
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-current.xsd
http://www.mulesoft.org/schema/mule/core http://www.mulesoft.org/schema/mule/core/current/mule.xsd">
    <munit:config name="munit" doc:name="MUnit configuration" mock-connectors="false" mock-inbounds="false"/>
    <spring:beans>
        <spring:import resource="classpath:interface.xml"/>
        <spring:import resource="classpath:orders-implementation.xml"/>
        <spring:import resource="classpath:global.xml"/>
        <spring:import resource="classpath:error-handling.xml"/>
        <spring:import resource="classpath:poll-tirehub-cache-auth-token-refresh.xml"/>
        <spring:import resource="classpath:brandmodelinfo.xml"/>
        <spring:import resource="classpath:locationinfo.xml"/>
        <spring:import resource="classpath:lookupcommondealers.xml"/>
        <spring:import resource="classpath:lookupinvoices.xml"/>
        <spring:import resource="classpath:physicalinvoices.xml"/>
        <spring:import resource="classpath:poll-auth-token-refresh.xml"/>
        <spring:import resource="classpath:ecommerceiteminfo.xml"/>
        <spring:import resource="classpath:inventory-check-implementation.xml"/>
    </spring:beans>
    <munit:test name="_orderGET:/{orderNo}/{dealerCode}:CoreAPI-configTest" description="Test">
        <munit:set payload="#[]" doc:name="Set Message">
            <munit:inbound-properties>
                <munit:inbound-property key="http.uri.params" value="#[{&quot;orderNo&quot;:&quot;2204203&quot;,&quot;dealerCode&quot;: &quot;333832&quot;}]" mimeType="application/java"/>
            </munit:inbound-properties>
        </munit:set>
        <flow-ref name="get:/{orderNo}/{dealerCode}:CoreAPI-config" doc:name="Flow-ref to get:/{orderNo}/{dealerCode}:CoreAPI-config"/>
        <munit:assert-not-null doc:name="Assert Not Null Payload"/>
    </munit:test>
</mule>
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
orderStatus_Post.xml
========================
<?xml version="1.0" encoding="UTF-8"?>
<mule xmlns="http://www.mulesoft.org/schema/mule/core" xmlns:doc="http://www.mulesoft.org/schema/mule/documentation" xmlns:munit="http://www.mulesoft.org/schema/mule/munit" xmlns:spring="http://www.springframework.org/schema/beans" xmlns:core="http://www.mulesoft.org/schema/mule/core" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.mulesoft.org/schema/mule/munit http://www.mulesoft.org/schema/mule/munit/current/mule-munit.xsd
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-current.xsd
http://www.mulesoft.org/schema/mule/core http://www.mulesoft.org/schema/mule/core/current/mule.xsd">
      <munit:config doc:name="Munit configuration" mock-connectors="false" mock-inbounds="false"/>
    <spring:beans>
        <spring:import resource="classpath:interface.xml"/>
         <spring:import resource="classpath:orders-implementation.xml"/>
        <spring:import resource="classpath:global.xml"/>
        <spring:import resource="classpath:error-handling.xml"/>
        <spring:import resource="classpath:poll-tirehub-cache-auth-token-refresh.xml"/>
        <spring:import resource="classpath:brandmodelinfo.xml"/>
        <spring:import resource="classpath:locationinfo.xml"/>
        <spring:import resource="classpath:lookupcommondealers.xml"/>
        <spring:import resource="classpath:lookupinvoices.xml"/>
        <spring:import resource="classpath:physicalinvoices.xml"/>
        <spring:import resource="classpath:poll-auth-token-refresh.xml"/>
        <spring:import resource="classpath:ecommerceiteminfo.xml"/>
        <spring:import resource="classpath:inventory-check-implementation.xml"/>
    </spring:beans>
    <munit:test name="orderStatus_Post-post:/order:application/json:CoreAPI-configTest" description="Test">
        <munit:set payload="#[getResource('sample_data/Order_status.json').asString()]" doc:name="Set Message" mimeType="application/json">
        </munit:set>
        <flow-ref name="post:/order:application/json:CoreAPI-config" doc:name="Flow-ref to post:/order:application/json:CoreAPI-config"/>
        <munit:assert-not-null doc:name="Assert Not Null Payload"/>
    </munit:test>
</mule>
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
physicalinvoicesummaries_POST.xml
=====================================

<?xml version="1.0" encoding="UTF-8"?>
<mule xmlns="http://www.mulesoft.org/schema/mule/core" xmlns:doc="http://www.mulesoft.org/schema/mule/documentation" xmlns:munit="http://www.mulesoft.org/schema/mule/munit" xmlns:spring="http://www.springframework.org/schema/beans" xmlns:core="http://www.mulesoft.org/schema/mule/core" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.mulesoft.org/schema/mule/munit http://www.mulesoft.org/schema/mule/munit/current/mule-munit.xsd
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-current.xsd
http://www.mulesoft.org/schema/mule/core http://www.mulesoft.org/schema/mule/core/current/mule.xsd">
    <munit:config doc:name="Munit configuration" mock-connectors="false" mock-inbounds="false"/>
    <spring:beans>
        <spring:import resource="classpath:interface.xml"/>
         <spring:import resource="classpath:orders-implementation.xml"/>
        <spring:import resource="classpath:global.xml"/>
        <spring:import resource="classpath:error-handling.xml"/>
        <spring:import resource="classpath:poll-tirehub-cache-auth-token-refresh.xml"/>
        <spring:import resource="classpath:brandmodelinfo.xml"/>
        <spring:import resource="classpath:locationinfo.xml"/>
        <spring:import resource="classpath:lookupcommondealers.xml"/>
        <spring:import resource="classpath:lookupinvoices.xml"/>
        <spring:import resource="classpath:physicalinvoices.xml"/>
        <spring:import resource="classpath:poll-auth-token-refresh.xml"/>
        <spring:import resource="classpath:ecommerceiteminfo.xml"/>
        <spring:import resource="classpath:inventory-check-implementation.xml"/>
    </spring:beans>
    <munit:test name="physicalinvoicesummaries_POST-post:/physicalinvoicesummaries:application/json:CoreAPI-configTest" description="Test">
        <munit:set payload="#[getResource('sample_data/physicalinvoicesummaries.json').asString()]" mimeType="application/json" doc:name="Set Message"/>
        <flow-ref name="post:/physicalinvoicesummaries:application/json:CoreAPI-config" doc:name="Flow-ref to post:/physicalinvoicesummaries:application/json:CoreAPI-config"/>
        <munit:assert-not-null doc:name="Assert Not Null Payload"/>
    </munit:test>
</mule>
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

invoicesummaries_POST.xml
=============================

<?xml version="1.0" encoding="UTF-8"?>
<mule xmlns="http://www.mulesoft.org/schema/mule/core" xmlns:doc="http://www.mulesoft.org/schema/mule/documentation" xmlns:munit="http://www.mulesoft.org/schema/mule/munit" xmlns:spring="http://www.springframework.org/schema/beans" xmlns:core="http://www.mulesoft.org/schema/mule/core" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.mulesoft.org/schema/mule/munit http://www.mulesoft.org/schema/mule/munit/current/mule-munit.xsd
http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-current.xsd
http://www.mulesoft.org/schema/mule/core http://www.mulesoft.org/schema/mule/core/current/mule.xsd">
      <munit:config doc:name="Munit configuration" mock-connectors="false" mock-inbounds="false"/>
    <spring:beans>
        <spring:import resource="classpath:interface.xml"/>
         <spring:import resource="classpath:orders-implementation.xml"/>
        <spring:import resource="classpath:global.xml"/>
        <spring:import resource="classpath:error-handling.xml"/>
        <spring:import resource="classpath:poll-tirehub-cache-auth-token-refresh.xml"/>
        <spring:import resource="classpath:brandmodelinfo.xml"/>
        <spring:import resource="classpath:locationinfo.xml"/>
        <spring:import resource="classpath:lookupcommondealers.xml"/>
        <spring:import resource="classpath:lookupinvoices.xml"/>
        <spring:import resource="classpath:physicalinvoices.xml"/>
        <spring:import resource="classpath:poll-auth-token-refresh.xml"/>
        <spring:import resource="classpath:ecommerceiteminfo.xml"/>
        <spring:import resource="classpath:inventory-check-implementation.xml"/>
    </spring:beans>
    <munit:test name="invoicesummaries_POST-post:/invoicesummaries:application/json:CoreAPI-configTest" description="Test">
        <munit:set payload="#[getResource('sample_data/invoicesummaries.json').asString()]" mimeType="application/json" doc:name="Set Message"/>
        <flow-ref name="post:/invoicesummaries:application/json:CoreAPI-config" doc:name="Flow-ref to post:/invoicesummaries:application/json:CoreAPI-config"/>
        <munit:assert-not-null doc:name="Assert Not Null Payload"/>
    </munit:test>
</mule>

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



