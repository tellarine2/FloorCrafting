function generateCommands() {
    const ingredient1 = document.getElementById('ingredient1').value.trim();
    const ingredient1Count = parseInt(document.getElementById('ingredient1Count').value) || 1;
    const ingredient2 = document.getElementById('ingredient2').value.trim();
    const ingredient2Count = parseInt(document.getElementById('ingredient2Count').value) || 1;
    const result = document.getElementById('result').value.trim();
    const resultCount = parseInt(document.getElementById('resultCount').value) || 1;
    const resultNBT = document.getElementById('resultNBT').value.trim();

    if (ingredient1 && ingredient2 && result) {
        let nbtData = resultNBT ? `,tag:{${resultNBT}}` : '';
        const commands = `
tag @e[nbt={OnGround:1b,Item:{id:"minecraft:${ingredient1}",Count:${ingredient1Count}b}}] add craft1
tag @e[nbt={OnGround:1b,Item:{id:"minecraft:${ingredient2}",Count:${ingredient2Count}b}}] add craft2
execute as @e[tag=craft1] at @e[tag=craft2,distance=..1] run summon item ~ ~ ~ {Tags:["itemkill1"],PickupDelay:20,Item:{id:"minecraft:${result}",Count:${resultCount}b${nbtData}}}
execute at @e[tag=craft1] as @e[tag=craft2,distance=..1] run particle minecraft:happy_villager ~ ~.4 ~ .2 .2 .2 0 15
execute at @e[tag=itemkill1] run playsound minecraft:entity.experience_orb.pickup master @a[distance=..10] ~ ~ ~ 1 1 1
execute at @e[tag=itemkill1] run kill @e[tag=craft1,distance=..1]
execute at @e[tag=itemkill1] run kill @e[tag=craft2,distance=..1]
tag @e[type=item] remove itemkill1
        `;

        document.getElementById('commandsOutput').innerHTML = `
<pre>${commands}</pre>
        `;
    } else {
        alert('Please enter all required fields.');
    }
}
