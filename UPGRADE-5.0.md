UPGRADE FROM 4.x to 5.0
=======================

Config
------

 * Added the `getChildNodeDefinitions()` method to `ParentNodeDefinitionInterface`.

Console
-------

 * Removed the `setCrossingChar()` method in favor of the `setDefaultCrossingChar()` method in `TableStyle`.

EventDispatcher
---------------

 * The `TraceableEventDispatcherInterface` has been removed.

FrameworkBundle
---------------

 * Removed support for `bundle:controller:action` and `service:action` syntaxes to reference controllers. Use `serviceOrFqcn::method`
   instead where `serviceOrFqcn` is either the service ID when using controllers as services or the FQCN of the controller.

   Before:

   ```yml
   bundle_controller:
       path: /
       defaults:
           _controller: FrameworkBundle:Redirect:redirect

   service_controller:
       path: /
       defaults:
           _controller: app.my_controller:myAction
   ```

   After:

   ```yml
   bundle_controller:
       path: /
       defaults:
           _controller: Symfony\Bundle\FrameworkBundle\Controller\RedirectController::redirectAction

   service_controller:
       path: /
       defaults:
           _controller: app.my_controller::myAction
   ```

 * Removed `Symfony\Bundle\FrameworkBundle\Controller\ControllerNameParser`.
 * Warming up a router in `RouterCacheWarmer` that does not implement the `WarmableInterface` is not supported anymore.
 * The `RequestDataCollector` class has been removed. Use the `Symfony\Component\HttpKernel\DataCollector\RequestDataCollector` class instead.

HttpFoundation
--------------

 * The `$size` argument of the `UploadedFile` constructor has been removed.
 * The `getClientSize()` method of the `UploadedFile` class has been removed.

Security
--------

 * The `ContextListener::setLogoutOnUserChange()` method has been removed.
 * The `Symfony\Component\Security\Core\User\AdvancedUserInterface` has been removed.

SecurityBundle
--------------

 * The `logout_on_user_change` firewall option has been removed.
 * The `switch_user.stateless` firewall option has been removed.
 * The `SecurityUserValueResolver` class has been removed.

Translation
-----------

 * The `FileDumper::setBackup()` method has been removed.
 * The `TranslationWriter::disableBackup()` method has been removed.

TwigBundle
----------

 * The default value (`false`) of the `twig.strict_variables` configuration option has been changed to `%kernel.debug%`.

Validator
--------

 * The `Email::__construct()` 'strict' property has been removed. Use 'mode'=>"strict" instead.
 * Calling `EmailValidator::__construct()` method with a boolean parameter has been removed, use `EmailValidator("strict")` instead.
 * Removed the `checkDNS` and `dnsMessage` options from the `Url` constraint.

Workflow
--------

 * `add` method has been removed use `addWorkflow` method in `Workflow\Registry` instead.
 * `SupportStrategyInterface` has been removed, use `WorkflowSupportStrategyInterface` instead.
 * `ClassInstanceSupportStrategy` has been removed, use `InstanceOfSupportStrategy` instead.
