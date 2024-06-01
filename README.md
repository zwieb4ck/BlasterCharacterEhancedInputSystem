# Enhanced Input System for Unreal Engine Characters

This is an example of how to use the Enhanced Input System for the Blaster Character for the Unreal Engine 5 C++ Multiplayer Shooter created by Stephen Ulibarri.

Since the old input system is now deprecated and cannot be used with current versions (5.4.1 at the time of creation), you need to use the enhanced input system.

To do this, follow these steps:

## Setting up the Input Actions
- Right-click in your content browser and select Input/Input Action. Name it IA_Move. Select `Axis2D (Vector2D)` as the Value Type.
- Repeat this for a file called IA_Look. It is important that you select `Axis2D (Vector2D)`.
- Create another input action called IA_Jump. Here, the value type needs to be `Digital (Bool)`.

## Setting up the Mapping Context
### Movement
- Right-click in your content browser and go to Input/Input Mapping Context. Give it a name; in this example, IMC_Default.
- Create a new mapping by clicking the + next to `Mapping`.
- Select IA_Move.
- Create bindings for "W", "A", "S", and "D", and add the following modifiers to the bindings:
    - W: `Swizzle Input Axis Values`
    - S: `Swizzle Input Axis Values` and `Negate`
    - A: `Negate`
    - D: Does not need any modifiers.

### Look
- Add a mapping and select IA_Look.
- For the binding, select `Mouse XY 2D-Axis`.
- Add the `Negate` modifier.

### Jump
- Add a new mapping and select IA_Jump.
- Since this is just a button press, we do not need any modifiers.

## Adding the Assets to Your Blueprint
When creating a BP_Character, you need to select your BlasterCharacter.cpp as the Parent Class. All needed declarations and imports can be found in this repository. Check your Class Settings to ensure this is the case. If everything is compiled correctly, you should be able to assign your mapping context and your actions to the corresponding slots.

![Asset selection in Editor](assign-in-editor.png)