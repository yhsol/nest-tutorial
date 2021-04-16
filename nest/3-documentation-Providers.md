# Providers

- Many of the basic Nest classes may be treated as a provider -
  services, repositories, factories, helpers, and so on.
- The main idea of a provider is that it can **inject** dependencies;
- this means objects can create various relationships with each other,
  and the function of "wiring up" instances of objects can largely be delegated to the Nest runtime system.
- Controllers should handle HTTP requests and
  delegate more complex tasks to **providers**.
  Providers are plain JavaScript classes that are declared as `providers` in a module.
  ```
  Controller (handle HTTP requests) ----(more complext thing)----> Provider
  ```

## Services

- Let's start by creating a simple `CatsService`.
- This service will be responsible for data storage and retrieval, and is designed to be used by the `CatsController`, so it's a good candidate to be defined as a provider.

Filename: cats.service.ts

```ts
```

## Dependency injection

- Nest is built around the strong design pattern commonly known as **Dependency injection**.
- In the example below, Nest will resolve the `catsService` by creating and returning an instance of `CatsService` (or, in the normal case of a singleton, returning the existing instance if it has already been requested elsewhere).
  This dependency is resolved and passed to your controller's constructor (or assigned to the indicated property):

```ts
  constructor(private: catsService: CatsService) {}
```

## Scopes

- Providers normally have a lifetime ("scope") synchronized with the application lifecycle.
- When the application is bootstrapped, every dependency must be resolved, and therefore every provider has to be instantiated.
- Similarly, when the application shuts down,
  each provider will be destroyed. However, there are ways to make your provider lifetime **request-scoped** as well. You can read more about these techniques [here](https://docs.nestjs.com/fundamentals/injection-scopes).

## Custom providers

- Nest ahs a built-in inversion of control ("IoC") container that resolves relationship between providers.
- This feature undelies the dependency injection feature described above,
  but is in fact far more powerful than what we've described so far.
  there are several ways to defined a provider:
  you can use plain values, classes, and either asynchronous or synchronous factories. More example are provied [here](https://docs.nestjs.com/fundamentals/custom-providers).

## Optional providers
