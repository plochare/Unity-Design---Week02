# GameObjects & Components

The fundamental **GameObject–Component** architecture in Unity, with diagrams and examples.

---

## 📌 Overview
Unity uses a **composition-based design**, where:
- **GameObjects** are the basic building blocks of a scene.
- **Components** are the modular behaviors and properties you attach to GameObjects.

Together, they form the foundation of every Unity project.

- **Unity Scene Diagram**:  

[![Unity Scene composition](images/scene.png)

---

## 📌 GameObjects
- The **basic container** in Unity.
- Represents anything in your scene: characters, props, cameras, UI, lights.
- Always includes a **Transform Component** (position, rotation, scale).

👉 Think of a **GameObject** as an **empty box** that gains functionality only when you add Components.

- **Unity GameObject Diagram **:  

[![Unity Game Object](images/gameobject.png)

---

## 📌 Components
- **Behavioral building blocks** that define *what a GameObject does*.
- Examples:
  - `Mesh Renderer` → makes an object visible.
  - `Rigidbody` → enables physics.
  - `Collider` → defines physical boundaries.
  - `Audio Source` → plays sounds.
  - `MonoBehaviour` scripts → add custom logic.

👉 Think of **Components** as **ingredients** you add to your GameObject to make it useful.

- **Unity Components Diagram **:  

[![Unity Components](images/hierarchy.png)

---

## ⚙️ How They Work Together
Every GameObject starts with a `Transform`.  
You can then attach multiple Components to build its full behavior:



# Data Types and Variables

A beginner-friendly guide introducing the core foundations of C# used in Unity game development.

---

## 📌 Data Types

A **data type** determines:

* What operations you can perform on data
* The interpretation of the data
* How much memory it occupies ([Circuit Stream][1])

Though C# offers over ten data types, only the most commonly used ones are needed for Unity development,

**Pro tip:**

* Use **double quotes** for strings.
* Add an **“f”** suffix for float literals (e.g., `9.99f`).([Circuit Stream][1])

---

## 📌 Variables

Variables are essentially “named boxes” that store data for use elsewhere in your code. Each variable must have:

1. A **type**
2. A **name**
3. A trailing **semicolon** to mark the end of the statement
4. Optionally, an **inline comment** using `//` for clarity 

Naming best practices: Stick to Latin letters and follow C# naming conventions.

---

## Type Conversion

Sometimes you need to convert between data types, such as:

* Displaying numbers as text

* Using `float` values with UI components expecting `int`

* Parsing user-input strings as numbers ([Circuit Stream][1])

* **Implicit conversion** occurs automatically—only if there's no risk of data loss. Otherwise, it fails.

* **Explicit conversion**, or **casting**, is required for potentially lossy conversions (e.g., converting `float` → `int`). For example:

  ````csharp
  int myInt = (int)myFloat;
  ``` :contentReference[oaicite:8]{index=8}
  ```
  ````

---

## 📌 Arithmetic Operators & Order of Operations

You can use standard arithmetic operators (e.g., `+`, `-`, `*`, `/`) on numeric variables. C# follows familiar math precedence rules—multiplication and division are evaluated before addition and subtraction.

---

## Example: Integer vs Float Division

```csharp
int result1 = 5 / 2;        // result1 == 2
float result2 = 5.0f / 2;   // result2 == 2.5f
float result3 = 5 / 2.0f;   // result3 == 2f (because 5/2 is int division first)
```

Explanation:

* **Line 1**: Both operands are `int`, so result is truncated to `2`.
* **Line 2**: Using a float operand yields a `float` result of `2.5f`.
* **Line 3**: Although one operand is `float`, the division is still performed as integer division first, resulting in `2f`—this demonstrates that data type influences evaluation order.([Circuit Stream][1])

**Key takeaway:** Pay careful attention to data types during operations. C# promotes to the “largest” type for calculations.

---

Here’s a polished and expanded **GitHub-style README** based on the Awesome Tuts blog post **“C# Programming With Unity – Conditional Statements”**. The content is beginner-friendly and designed to function as a standalone tutorial, ideal for a Unity learning repository.

---

# Conditional Statements

A foundational guide to understanding and using conditional logic (`if`, `else`, `else if`) in Unity C# programming.

---

## 📌 What Are Conditional Statements?

Conditional statements allow your code to execute specific blocks based on whether a condition evaluates to **true** or **false**. They're essential for branching logic, handling events, and making your game interactive.

---

## Anatomy of an `if` Statement

The basic structure in C# and Unity is straightforward:

```csharp
if (CONDITION)
{
    // Execute this code block when CONDITION == true
}
```

* `CONDITION` must be a boolean expression (`true` or `false`).
* If the condition holds true, the enclosed block runs; otherwise, it's skipped. ([Anyone Can Learn To Make Games][1])

### Example:

```csharp
if (2 > 1)
{
    Debug.Log("This will always run!");
}
```

Here, `2 > 1` always evaluates to true, so the log fires every time. 

Or, using variables:

```csharp
float a = 3f;
float b = 4f;

if (a > b)
{
    Debug.Log("a is greater than b");
}
```

Since `3f` is not greater than `4f`, this block won't execute. 

---

## 📌 Comparison Operators You Can Use

Comparison operators enable nuanced checks:

* `<`  — Less than
* `>`  — Greater than
* `<=` — Less than or equal to
* `>=` — Greater than or equal to
* `==` — Equal to
* `!=` — Not equal to ([Anyone Can Learn To Make Games][2], [W3Schools][3])

These are invaluable for comparing scores, positions, health values, etc.

---

## `if` … `else` Structures

Often, you want a fallback when the `if` condition fails. The `else` clause handles that:

```csharp
if (playerHealth <= 0)
{
    // Handle player's death
}
else
{
    // Continue the game
}
```

This ensures your code responds appropriately whether the player is alive or not. 

To manage multiple scenarios, you can chain conditions using `else if`:

```csharp
if (health >= 75)
{
    Debug.Log("You're in great shape!");
}
else if (health >= 25)
{
    Debug.Log("You're hurt, be careful!");
}
else
{
    Debug.Log("You’re near defeat!");
}
```

This creates a clear decision flow for varying health levels.

---

## 🚀 Practical Unity Examples

Here are practical uses of conditional statements in Unity contexts:

* Checking enemy status:

  ```csharp
  if (!enemy.isAlive)
  {
      Destroy(enemy.gameObject);
  }
  ```

* Verifying player input:

  ```csharp
  if (Input.GetKeyDown(KeyCode.Space))
  {
      Jump();
  }
  ```

* Managing inventory capacity:

  ```csharp
  if (inventorySlots >= maxSlots)
  {
      ShowInventoryFullWarning();
  }
  ```

These examples reflect typical Unity game logic scenarios.

---

## Advanced Flow Control

Unity and C# offer additional tools:

* **`switch` statements** — Efficiently handle many discrete values:

  ```csharp
  switch (playerState)
  {
      case PlayerState.Idle:
          Idle();
          break;
      case PlayerState.Running:
          Run();
          break;
      default:
          Jump();
          break;
  }
  ```

* **Ternary operator** (`?:`) — Compact conditionals:

  ```csharp
  string status = (health > 0) ? "Alive" : "Dead";
  ```

* **Short-circuit logic** (`&&`, `||`) — Safe state checks:

  ```csharp
  if (player != null && player.isReady)
  {
      player.StartGame();
  }
  ```

These constructs are powerful companions once you’ve mastered the basics.

---

## Best Practices & Tips

* Keep boolean conditions **clear and concise** for readability.

* Favor **`else if` over nested `if` statements** to reduce complexity.

* Employ **early returns** for cleaner flows:

  ```csharp
  if (health <= 0)
  {
      HandleDeath();
      return;
  }
  // Continue healthy logic
  ```

* Use **comments** to clarify conditional logic intent when needed.

---

# C# Unity - Beginner Scripting Tutorials
https://www.youtube.com/playlist?list=PLX2vGYjWbI0S9-X2Q021GUtolTqbUBB9B

---

# Roll-a-Ball Game! Beginner learning project
https://learn.unity.com/course/roll-a-ball?version=6.0


# Assignment Week #2 - Flappy Bird Game https://www.youtube.com/watch?v=XtQMytORBmM



